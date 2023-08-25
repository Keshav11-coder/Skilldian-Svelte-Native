<!--
  reminder how to use git

  git init
  git remote add origin <url>
  git checkout -b new-branch-name origin/main //new branch
  git add .
  git commit -m "message"
  git push origin branch-name
-->
<script>
  import {
    Application,
    StackLayout,
    verticalAlignmentProperty,
  } from "@nativescript/core";

  const isDarkMode =
    Application.android?.context?.getResources().getConfiguration().uiMode &
    android.content.res.Configuration.UI_MODE_NIGHT_MASK;

  import { onMount } from "svelte";
  import IconInitiator from "./icons/IconInitiator.svelte";

  export let page = 0;

  let navVisible = true;
  let lastScrollPosition = 0;
  let scrollPosition = 0;
  let scrollView;

  let icons = [
    {
      GlobalName: "Heart",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 0,
      ListIndex: 0,
    },
    {
      GlobalName: "Share",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 1,
      ListIndex: 1,
    },
    {
      GlobalName: "Bookmark",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 2,
      ListIndex: 2,
    },
    {
      GlobalName: "More",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 3,
      ListIndex: 3,
    },
  ];

  let BottomNav = [
    {
      GlobalName: "Home",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 5,
    },
    {
      GlobalName: "Add",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 6,
    },
    {
      GlobalName: "Chat",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 4,
    },
  ];

  onMount(() => {
    scrollView.addEventListener("scroll", handleScroll);
  });

  function handleScroll(event) {
    scrollPosition = event.object.verticalOffset;

    if (scrollPosition > lastScrollPosition) {
      navVisible = false;
    } else if (scrollPosition < lastScrollPosition) {
      navVisible = true;
    }

    lastScrollPosition = scrollPosition;
    console.log(navVisible);
  }

  let responseData = "";
  let items = [];
  let data = [];

  async function get_items() {
    const response = await fetch(
      "http://192.168.1.19:3000/api?database=skilldian&collection=feed&amount=20"
    ); // takes a long time to load, thats why the weird screen before content. try to fix it by binding a variable to the app.svelte
    //and then loading a loadingscreen first and after the variable has been updated yo ufinally show the content. second option is to just leave it like that, and think of more if the first does not work.
    data = await response.json();
    responseData = JSON.stringify(data, null, 2);
    items = data;
  }

  // [0:homeTab, 1:searchPage, 2:recentNotifications, 3:jobDetailsPage, 4:addPostTab, 5:messagesTab, 6:settingsTab]
  export let frame = 0;

  function pageSelector(index) {
    page = index;
    console.log(page);
  }

  function ItemExtend(index) {
    items[index].IsExtended = items[index].IsExtended ? false : true;
  }

  function TapNull(event) {}

  setTimeout(() => {
    get_items();
  }, 1000);
</script>

<page
  class="page-css"
  backgroundColor={isDarkMode === 32 ? "#232125" : "#cfcfcf"}
  actionBarHidden="true"
>
  <absoluteLayout
    width="100%"
    height="100%"
    backgroundColor={items.length === 0 ? "" : ""}
  >
    <!--start-->
    <!--Content-->
    <stackLayout width="100%" height="100%">
      <scrollView
        orientation="vertical"
        bind:this={scrollView}
        class="hide"
        height="100%"
      >
        {#if frame === 0}
          {#if items.length !== 0}
            <stacklayout>
              <stackLayout
                orientation="horizontal"
                height="50"
                backgroundColor="#232125"
                marginBottom="0"
              />

              <stackLayout
                on:scroll={handleScroll}
                backgroundColor={isDarkMode === 32 ? "#111112" : "#cfcfcf"}
                orientation="vertical"
              >
                <!--{#if items !== []}-->
                {#each items as item, index}
                  <stackLayout
                    orientation="vertical"
                    width="100%"
                    backgroundColor="#232125"
                    padding="10"
                    class="item"
                  >
                    <stackLayout
                      orientation="horizontal"
                      width="100%"
                      on:tap={() => ItemExtend(index)}
                      verticalAlignment="top"
                    >
                      {#if item.type === "premium"}
                        <stackLayout orientation="vertical">
                          <image
                            src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/s_defect.png"
                            width={item.type === "premium" ? "60vw" : "90vw"}
                            height={item.type === "premium" ? "60vw" : "90vw"}
                            id="im-img"
                            horizontalAlignment="center"
                            borderRadius="8vw"
                            borderTopRightRadius="0vw"
                          />
                          <stackLayout width="60vw" height="40vw" />
                        </stackLayout>
                      {:else if item.type !== "premium"}
                        <stackLayout orientation="vertical">
                          <image
                            src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/s_defect.png"
                            width={item.type === "premium" ? "60vw" : "60vw"}
                            height={item.type === "premium" ? "60vw" : "60vw"}
                            id="im-img"
                            verticalAlignment="center"
                            horizontalAlignment="center"
                            borderRadius="8vw"
                            borderTopRightRadius="0vw"
                          />
                        </stackLayout>
                      {/if}
                      <stackLayout width="100%" height={item.type ==="premium" ? "100" : "60"} verticalAlignment="top" horizontalAlignment="left">
                        <stackLayout
                          height="100%"
                          width="100%"
                          paddingLeft="8"
                          ><label text="Web Developer" fontSize="18" />
                          <label text={item.cc} fontSize="15" opacity="0.7" />
                          {#if item.type === "premium"}
                            <stackLayout marginTop="3">
                              <label text={item.description} textWrap="true" />
                            </stackLayout>
                          {/if}
                        </stackLayout>
                      </stackLayout>
                    </stackLayout>
                    <stacklayout
                      orientation="horizontal"
                      width="90%"
                      backgroundColor="#353139"
                      borderRadius="12px"
                      marginTop="12"
                      class={item.IsExtended ? "Extend-I" : "Shrink-I"}
                    >
                      {#each icons as icon}
                        <absoluteLayout
                          width="25%"
                          height="100%"
                          opacity="0.9"
                          borderTopLeftRadius={icon.ListIndex === 0
                            ? "12px"
                            : "0px"}
                          borderBottomLeftRadius={icon.ListIndex === 0
                            ? "12px"
                            : "0px"}
                          borderTopRightRadius={icon.ListIndex ===
                          icons.length - 1
                            ? "12px"
                            : "0px"}
                          borderBottomRightRadius={icon.ListIndex ===
                          icons.length - 1
                            ? "12px"
                            : "0px"}
                          ><IconInitiator
                            iconColor={icon.Color}
                            iconSize={0.85}
                            iconIndex={icon.Index}
                            IconActivated={icon.Active}
                          /></absoluteLayout
                        >
                        <stackLayout
                          width="0.5"
                          height="80%"
                          backgroundColor="gray"
                        />
                      {/each}
                    </stacklayout>
                  </stackLayout>
                {/each}
              </stackLayout>
            </stacklayout>
          {:else if items.length === 0}
            <stackLayout
              width="80"
              height="80"
              orientation="horizontal"
              backgroundColor="transparent"
            >
              <image
                src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/skilldian.png"
                width="100%"
                height="100%"
                borderRadius="20%"
                opacity="0.6"
              />
            </stackLayout>
          {/if}
        {:else if frame === 1}{/if}
      </scrollView>
    </stackLayout>
    <!--end-->

    <!--start-->
    <!--navs-->
    {#if items.length !== 0}
      <stackLayout width="100%" height="100%">
        <!--start-->
        <!--TopNav-->
        <dockLayout height="50%" width="100%">
          <stackLayout width="100%" dock="top" verticalAlignment="top">
            {#if frame === 0}
              <stackLayout
                orientation="horizontal"
                height="50"
                class="action-Bar {!navVisible ? 'nav-d' : 'nav-a'}"
                backgroundColor="#232125"
                horizontalAlignment="stretch"
              >
                <dockLayout>
                  <stackLayout
                    width="15%"
                    height="50"
                    dock="left"
                    verticalAlignment="center"
                  >
                    <image
                      src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/ocd-f.jpg"
                      width="37"
                      height="37"
                      id="im-img"
                      verticalAlignment="center"
                      horizontalAlignment="center"
                      borderRadius="50%"
                      dock="left"
                    />
                  </stackLayout>
                  <stackLayout
                    width="72%"
                    height="50"
                    verticalAlignment="center"
                  >
                    <textField
                      hint="search"
                      editable="true"
                      width="96%"
                      height="35"
                      paddingLeft="10"
                      fontSize="15"
                      backgroundColor="#ffffff47"
                      borderRadius="5vw"
                      borderBottomColor="transparent"
                      style="placeholder-color:white"
                      on:tap={() => (frame = 1)}
                    />
                  </stackLayout>
                  <stackLayout
                    width="13%"
                    height="50"
                    dock="right"
                    verticalAlignment="center"
                  >
                    <stackLayout
                      width="37"
                      height="37"
                      verticalAlignment="center"
                    >
                      <image
                        src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/bell.png"
                        width="60%"
                        height="60%"
                        id="im-img"
                        verticalAlignment="center"
                        horizontalAlignment="center"
                        dock="right"
                      />
                    </stackLayout>
                  </stackLayout>
                </dockLayout>
              </stackLayout>
            {:else if frame === 1}
              <stackLayout
                orientation="horizontal"
                height="50"
                class="action-Bar {!navVisible ? 'nav-d' : 'nav-a'}"
                backgroundColor="#232125"
                horizontalAlignment="stretch"
                borderBottomWidth="0.5"
                borderBottomColor="gray"
              >
                <dockLayout>
                  <stackLayout
                    width="15%"
                    height="50"
                    dock="left"
                    verticalAlignment="center"
                  >
                    <image
                      src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/ocd-f.jpg"
                      width="37"
                      height="37"
                      id="im-img"
                      verticalAlignment="center"
                      horizontalAlignment="center"
                      borderRadius="50%"
                      dock="left"
                    />
                  </stackLayout>
                  <stackLayout
                    width="72%"
                    height="50"
                    verticalAlignment="center"
                  >
                    <textField
                      hint="search"
                      editable="true"
                      width="96%"
                      height="35"
                      paddingLeft="10"
                      fontSize="15"
                      backgroundColor="#ffffff47"
                      borderRadius="5vw"
                      borderBottomColor="transparent"
                      style="placeholder-color:white"
                      on:tap={() => (frame = 1)}
                    />
                  </stackLayout>
                  <stackLayout
                    width="13%"
                    height="50"
                    dock="right"
                    verticalAlignment="center"
                  >
                    <stackLayout
                      width="37"
                      height="37"
                      verticalAlignment="center"
                    >
                      <image
                        src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/bell.png"
                        width="60%"
                        height="60%"
                        id="im-img"
                        verticalAlignment="center"
                        horizontalAlignment="center"
                        dock="right"
                      />
                    </stackLayout>
                  </stackLayout>
                </dockLayout>
              </stackLayout>
            {/if}
          </stackLayout>
        </dockLayout>
        <!--end-->

        <!--start-->
        <!--bottomNav-->
        <dockLayout height="50%" width="100%" marginTop="1">
          <stackLayout width="100%" dock="bottom" verticalAlignment="bottom"
            ><stackLayout width="100%" dock="bottom" height="50"
              ><stackLayout
                orientation="horizontal"
                height="100%"
                class="action-Bar {!navVisible ? 'nav-bd' : 'nav-ba'}"
                backgroundColor="#232125"
                horizontalAlignment="stretch"
              >
                {#each BottomNav as NavItem}
                  <absoluteLayout width="33%" height="40" opacity="0.8"
                    ><IconInitiator
                      iconColor={NavItem.Color}
                      iconSize={1.1}
                      iconIndex={NavItem.Index}
                      IconActivated={NavItem.Active}
                    /></absoluteLayout
                  >
                {/each}
              </stackLayout>
            </stackLayout>
          </stackLayout>
        </dockLayout>
        <!--end-->
      </stackLayout>
    {/if}
    <!--end-->
  </absoluteLayout>
</page>

<!--WORK LOG COMMENTS - started 8/20/23-->

<!--beta 1.0

icon not centering fix: try to work the icons towards the center, so they will automatically center in the absolute parent. 
its tough, but it might be a fix. fix: in the icon you put the size to 100% and in the outer you parent with a stackLayout and over that another absoluteLayout. the stackLayout has been set to 100% and vertical & horizontal alignment
in the child wrapper of the icon we decrease the sizes to try and port it to the middle. check code: IconInitiator, [icon].svelte, Home.svelte
              11:25 8/20/23 keshav @ Skilldian SN *FIXED

icon finish & icon dynamic customizable edit (line 586)
              22:16 8/21/23 keshav @ Skilldian SN *

comments cleanup; lines 712 => 435
              22:19 8/21/23 keshav @ Skilldian SN *

fix navbar resize problem; switched from double stackLayouts to dock layout and vertical-horizontal Alignment
resized the elements and ensured differential viewport support
              23:57 8/21/23 keshav @ Skilldian SN *FIXED*BUG

Color correct: fix discolored styles
              00:09 8/22/23 keshav @ Skilldian SN *FIXED*BUG
              LAST FIX; UPDATE RELEASED

-->
<!--beta 1.1
full content view support: fixed the spacing at the bottom of the frame, now full view on navbars hidden
              15:01 8/22/23 keshav @ Skilldian SN *FIXED*BUG

try to make the bottomnav a seperate thing so you do not need the spacing.. try to merge it with the content
to get it down automatically maybe? *this does not work
-
fix: stackLayout overlay over the scrollView, devide that into 2 docklayouts 50/50, then for each docklayout we have our navbars inside, and then position them accordingly
using verticalAlignment and dock="bottom/top"
              21:01 8/23/23 keshav @ Skilldian SN *FIXED

bottomNav finish: icons, resizable?, not blocking other components?; check fix above
              22:12 8/23/23 keshav @ Skilldian SN *FIXED

Interaction Bar spacing fix: add a little line to distinguish 
              16:17 8/24/23 keshav @ Skilldian SN *FIXED

Add loading screen: simmple skilldian logo to cover up loading of api
              13:17 8/25/23 keshav @ Skilldian SN *FIXED

Configure Api: add global API support to be accessible on entire network
              13:17 8/25/23 keshav @ Skilldian SN *FIXED

Create dummy job data database for api
              8/24/23 keshav @ Skilldian SN *FIXED

Add api to UI
              8/24/23 keshav @ Skilldian SN *FIXED
-->

<style>
  .action-Bar {
    height: 60;
    z-index: 4;
  }

  .hide {
    z-index: -5;
  }

  .nav-d {
    animation: NavHide ease-in-out 0.3s forwards;
  }
  .nav-a {
    animation: NavShow ease-in-out 0.3s forwards;
  }
  .nav-bd {
    animation: NavBottomHide ease-in-out 0.3s forwards;
  }
  .nav-ba {
    animation: NavBottomShow ease-in-out 0.3s forwards;
  }

  .Extend-I {
    animation: ExtendItemn cubic-bezier(0.47, 0, 0.745, 0.715) 0.1s forwards;
  }
  .Shrink-I {
    animation: ShrinkItemn cubic-bezier(0.47, 0, 0.745, 0.715) 0.1s forwards;
  }

  .page-css {
    border-top: 6px solid #3b2e98de;
    box-sizing: content-box;
  }

  .item {
    margin-top: 8vh;
  }

  @keyframes NavHide {
    /* slides up the topnav */
    0% {
      transform: translateY(0px);
    }
    100% {
      transform: translateY(-100px);
    }
  }

  @keyframes NavShow {
    0% {
      transform: translateY(-100px);
    }
    100% {
      transform: translateY(0px);
    }
  }

  @keyframes NavBottomHide {
    /* slides up the topnav */
    0% {
      transform: translateY(0px);
    }
    100% {
      transform: translateY(100px);
    }
  }

  @keyframes NavBottomShow {
    0% {
      transform: translateY(100px);
    }
    100% {
      transform: translateY(0px);
    }
  }

  @keyframes ExtendItemn {
    0% {
      height: 0;
    }
    100% {
      height: 40;
    }
  }

  @keyframes ShrinkItemn {
    0% {
      height: 40;
    }
    100% {
      height: 0;
    }
  }

  @keyframes ItemPopupHide {
    0% {
      transform: translateY(0px);
    }
    100% {
      transform: translateY(180px);
    }
  }

  @keyframes ItemPopupShow {
    0% {
      transform: translateY(180px);
    }
    100% {
      transform: translateY(0px);
    }
  }
</style>
