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
  import { Application, StackLayout } from "@nativescript/core";

  const isDarkMode =
    Application.android?.context?.getResources().getConfiguration().uiMode &
    android.content.res.Configuration.UI_MODE_NIGHT_MASK;

  import { onMount } from "svelte";
  import { scrollTo } from "svelte-native";
  import IconInitiator from "./icons/IconInitiator.svelte";

  export let page = 0;

  let navVisible = true;
  let lastScrollPosition = 0;
  let scrollPosition = 0;
  let scrollView;
  let restoreScroll;
  let scrollState = "vertical";

  console.log("TEST 1 PASSED: IMPORTS");

  let icons = [
    {
      GlobalName: "Heart",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 0,
    },
    {
      GlobalName: "Share",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 1,
    },
    {
      GlobalName: "Bookmark",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 2,
    },
    {
      GlobalName: "More",
      Color: "white",
      Active: false,
      Scale: 0.9,
      Index: 3,
    },
  ];

  console.log("TEST 2 PASSED: ICON SETUP*");

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

  function handleSwipe(event) {
    if (event.state === 3 && event.deltaX > 100) {
      elements.push("Element1");
    }
    console.log(elements);
  }

  console.log("scroll test pass");

  let items = [
    {
      url: "../s_defect.png",
      opp: "Web Developer",
      cc: "Amazon",
      oc: `red`,
      type: "premium",
      description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      Index: 0,
      IsExtended: true,
    },
    {
      url: "../s_defect.png",
      opp: "Web Developer",
      cc: "Amazon",
      oc: `red`,
      type: "free",
      description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      Index: 1,
      IsExtended: true,
    },
    {
      url: "../s_defect.png",
      opp: "Web Developer",
      cc: "Amazon",
      oc: `red`,
      type: "premium",
      description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      Index: 2,
      IsExtended: false,
    },
    {
      url: "../s_defect.png",
      opp: "Web Developer",
      cc: "Amazon",
      oc: `red`,
      type: "free",
      description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      Index: 3,
      IsExtended: false,
    },
    {
      url: "../s_defect.png",
      opp: "Web Developer",
      cc: "Amazon",
      oc: `red`,
      type: "free",
      description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      Index: 4,
      IsExtended: false,
    },
    {
      url: "../s_defect.png",
      opp: "Web Developer",
      cc: "Amazon",
      oc: `red`,
      type: "premium",
      description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      Index: 5,
      IsExtended: false,
    },
    {
      url: "../s_defect.png",
      opp: "Web Developer",
      cc: "Amazon",
      oc: `red`,
      type: "premium",
      description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      Index: 6,
      IsExtended: false,
    },
  ];

  function pageSelector(index) {
    page = index;
    console.log(page);
  }

  let ItemPopupInitiated = false;

  function ItemExtend(index) {
    console.log("extending current item .. hold up");
    items[index].IsExtended = items[index].IsExtended ? false : true;
  }

  function ItemPopup() {
    ItemPopupInitiated = true;
    console.log("done.");
  }
  console.log("test 5 passed - all tests complete");
</script>

<page
  class="page-css"
  backgroundColor={isDarkMode === 32 ? "#232125" : "#cfcfcf"}
  actionBarHidden="true"
>
  <stackLayout
    ><stackLayout
      orientation="horizontal"
      height="50"
      class="action-Bar {!navVisible ? 'nav-d' : 'nav-a'}"
      backgroundColor="#242327"
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
        <stackLayout width="72%" height="50" verticalAlignment="center">
          <textField
            hint="search here..."
            editable="true"
            width="96%"
            height="35"
            paddingLeft="10"
            fontSize="15"
            backgroundColor="#ffffff47"
            borderRadius="5vw"
            borderBottomColor="transparent"
            style="placeholder-color:white"
          />
        </stackLayout>
        <stackLayout
          width="13%"
          height="50"
          dock="right"
          verticalAlignment="center"
        >
        <stackLayout width="37"
        height="37" verticalAlignment="center">
          <image
            src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/bell.png"
            width= "60%"
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
    <scrollView
      orientation="vertical"
      bind:this={scrollView}
      class="hide"
      height="100%"
      marginTop="-60"
    >
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
          {#each items as item}
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
                on:tap={() => ItemExtend(item.Index)}
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
                <stackLayout height="100%" width="60%" paddingLeft="8"
                  ><label text="Web Developer" fontSize="18" />
                  <label text={item.cc} fontSize="15" opacity="0.7" />
                  {#if item.type === "premium"}
                    <stackLayout marginTop="3">
                      <label text={item.description} textWrap="true" />
                    </stackLayout>
                  {/if}
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
                  <absoluteLayout width="25%" height="100%"
                    ><IconInitiator
                      iconColor={icon.Color}
                      iconSize={0.85}
                      iconIndex={icon.Index}
                      IconActivated={icon.Active}
                    /></absoluteLayout
                  >
                {/each}
              </stacklayout>
            </stackLayout>
          {/each}
        </stackLayout>
      </stacklayout>
    </scrollView>
  </stackLayout></page
>

<!--WORK LOG COMMENTS - started 8/20/23-->

<!--beta 1.0

icon not centering fix: try to work the icons towards the center, so they will automatically center in the absolute parent. 
its tough, but it might be a fix. fix: in the icon you put the size to 100% and in the outer you parent with a stackLayout and over that another absoluteLayout. the stackLayout has been set to 100% and vertical & horizontal alignment
in the child wrapper of the icon we decrease the sizes to try and port it to the middle. check code: IconInitiator, [icon].svelte, Home.svelte
              11:25 8/20/23 keshav @ Skilldian SN *FIXED

icon finish & icon dynamic customizable edit (line 586)
              10:16 8/21/23 keshav @ Skilldian SN *

comments cleanup; lines 712 => 435
              10:19 8/21/23 keshav @ Skilldian SN *

fix navbar resize problem; switched from double stackLayouts to dock layout and vertical-horizontal Alignment
resized the elements and ensured differential viewport support
              11:57 8/21/23 keshav @ Skilldian SN *FIXED

Color correct: fix discolored styles
              12:09 8/22/23 keshav @ Skilldian SN *FIXED
              LAST FIX; UPDATE RELEASED

-->
<!--beta 1.1



-->


<style>
  .action-Bar {
    height: 60;
    z-index: 400;
  }

  .up {
    z-index: 500;
  }

  .nav-d {
    animation: NavHide ease-in-out 0.2s forwards;
  }
  .nav-a {
    animation: NavShow ease-in-out 0.2s forwards;
  }

  .Extend-I {
    animation: ExtendItemn cubic-bezier(0.47, 0, 0.745, 0.715) 0.1s forwards;
  }
  .Shrink-I {
    animation: ShrinkItemn cubic-bezier(0.47, 0, 0.745, 0.715) 0.1s forwards;
  }
  .PopupNone {
    animation: ItemPopupHide ease-in-out 0.2s forwards;
  }
  .PopupItem {
    animation: ItemPopupShow ease-in-out 0.2s forwards;
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
      margin-bottom: -260vw;
    }
    100% {
      margin-bottom: 0vw;
    }
  }

  @keyframes ItemPopupShow {
    0% {
      margin-bottom: 0vw;
    }
    100% {
      margin-bottom: -206vw;
    }
  }
</style>
