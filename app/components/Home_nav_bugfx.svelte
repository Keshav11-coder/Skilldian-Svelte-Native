<script>
    import { Application, StackLayout } from "@nativescript/core";
  
    const isDarkMode =
      Application.android?.context?.getResources().getConfiguration().uiMode &
      android.content.res.Configuration.UI_MODE_NIGHT_MASK;
  
    import { onMount } from "svelte";
    import { scrollTo } from "svelte-native";
  
    let navVisible = true;
    let lastScrollPosition = 0;
    let scrollPosition = 0;
    let scrollView;
    let restoreScroll;
    let scrollState = "vertical";
  
    onMount(() => {
      scrollView.addEventListener("scroll", handleScroll);
    });
  
    function handleScroll(event) {
      scrollPosition = event.object.verticalOffset;
  
      if (scrollPosition > lastScrollPosition) {
          navVisible = false;
      } else {
          navVisible = true;
      }
  
      lastScrollPosition = scrollPosition;
      console.log(navVisible);
    }
  
    function scrollToTop() {
      scrollTo(scrollView, 0, true);
    }
  
    let elements = [];
  
    function handleSwipe(event) {
      if (event.state === 3 && event.deltaX > 100) {
        elements.push("Element1");
      }
      console.log(elements);
    }
  
    let items = [
      {
        url: "../s_defect.png",
        opp: "Web Developer",
        cc: "Amazon",
        oc: `red`,
        type: "premium",
        description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      },
      {
        url: "../s_defect.png",
        opp: "Web Developer",
        cc: "Skilldian",
        type: "free",
      },
      {
        url: "../s_defect.png",
        opp: "Web Developer",
        cc: "Linkedin",
        oc: `red`,
        type: "premium",
        description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      },
      {
        url: "../s_defect.png",
        opp: "Web Developer",
        cc: "Amazon",
        oc: `red`,
        type: "premium",
        description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      },
      {
        url: "../s_defect.png",
        opp: "Web Developer",
        cc: "Skilldian",
        type: "free",
      },
      {
        url: "../s_defect.png",
        opp: "Web Developer",
        cc: "Linkedin",
        oc: `red`,
        type: "premium",
        description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      },
      {
        url: "../s_defect.png",
        opp: "Web Developer",
        cc: "Amazon",
        oc: `red`,
        type: "premium",
        description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      },
      {
        url: "../s_defect.png",
        opp: "Web Developer",
        cc: "Skilldian",
        type: "free",
      },
      {
        url: "../s_defect.png",
        opp: "Web Developer",
        cc: "Linkedin",
        oc: `red`,
        type: "premium",
        description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
      },
    ];
  </script>
  
  <page
    class="page-css"
    borderTopColor="#492dc9de"
    borderTopWidth="6"
    backgroundColor={isDarkMode === 32 ? "#343434" : "#cfcfcf"}
    actionBarHidden="true"
  >
  
      <!--<stackLayout orientation="horizontal" height="60vh">
        <button
          on:tap={() => console.log("works +left")}
          class="custom-button"
          width="36"
          height="36"
          backgroundImage="url('https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
          32
            ? 'bell.png'
            : 'bell_B.png'}')"
          backgroundSize="60% 60%"
          backgroundRepeat="no-repeat"
          backgroundPosition="center"
          marginRight="26%"
          borderRadius="5"
          backgroundColor="transparent"
        />
        <label fontSize="24" verticalAlignment="center">For you</label>
        <button
          on:tap={() => console.log("works +right")}
          class="custom-button"
          width="36"
          height="36"
          backgroundImage="url('https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
          32
            ? 'search.png'
            : 'search_B.png'}')"
          backgroundSize="60% 60%"
          backgroundRepeat="no-repeat"
          backgroundPosition="center"
          marginLeft="24%"
          borderRadius="5"
          backgroundColor="transparent"
        />
      </stackLayout>-->
  
  
    <dockLayout class="dock-content" verticalAlignment="bottom">
      <label
      text="bottom"
      dock="bottom"
      class="dock-bottom {navVisible ? 'bd-visible' : 'bd-closed'}"
      height="60"
    />
      <scrollView
        orientation="vertical"
        bind:this={scrollView}
        class="no-bounce"
        verticalAlignment="middle"
        height="100%"
      >
        <stackLayout
          on:scroll={handleScroll}
          padding="10"
          backgroundColor={isDarkMode === 32 ? "#343434" : "#cfcfcf"}
          class="pageContentisgood"
          orientation="vertical"
          borderColor="red"
          borderWidth="2px"
        >
        <stackLayout orientation="horizontal" height="60" dock="top" backgroundColor="#2b2b2c" class="action-Bar" borderRadius={!navVisible ? "50%" : ""} translateY="{!navVisible ? '0' : lastScrollPosition}">
          <button
            on:tap={() => console.log("works +left")}
            class="custom-button"
            width="36"
            height="36"
            backgroundImage="url('https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
            32
              ? 'bell.png'
              : 'bell_B.png'}')"
            backgroundSize="60% 60%"
            backgroundRepeat="no-repeat"
            backgroundPosition="center"
            marginRight="27.5%"
            borderRadius="5"
            backgroundColor="transparent"
          />
          <label fontSize="24" verticalAlignment="center">For you</label>
          <button
            on:tap={() => console.log("works +right")}
            class="custom-button"
            width="36"
            height="36"
            backgroundImage="url('https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
            32
              ? 'search.png'
              : 'search_B.png'}')"
            backgroundSize="60% 60%"
            backgroundRepeat="no-repeat"
            backgroundPosition="center"
            marginLeft="28%"
            borderRadius="5"
            backgroundColor="transparent"
          />
        </stackLayout>
          {#each items as item}
            <stackLayout
              orientation="horizontal"
              width="100%"
              height={item.type === "premium" ? "140vw" : "90vw"}
              class="item"
              on:pan={handleSwipe}
              ><!--{item.type === "premium" ? "140vw" : "90vw"}-->
              <stackLayout
                height="100%"
                width="60%"
                borderLeftColor="#492dc9de"
                borderLeftWidth="6"
                paddingLeft="8"
                ><label text="Web Developer" fontSize="22" />
                <label text={item.cc} fontSize="18" opacity="0.7" />
                {#if item.type === "premium"}
                  <stackLayout marginTop="3">
                    <label text={item.description} textWrap="true" />
                  </stackLayout>
                {/if}
              </stackLayout>
              <image
                src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/s_defect.png"
                width={item.type === "premium" ? "140vw" : "90vw"}
                height={item.type === "premium" ? "140vw" : "90vw"}
                id="im-img"
                verticalAlignment="center"
                horizontalAlignment="center"
                borderRadius="8vw"
              />
              {#if item.type === "premium"}
                <stackLayout
                  height="100%"
                  width="12%"
                  marginLeft="2%"
                  verticalAlignment="center"
                  horizontalAlignment="center"
                  borderRadius="8vw"
                  borderColor="#492dc9de"
                  borderWidth="4"
                />
              {:else if item.type !== "premium"}
                <stackLayout
                  height="100%"
                  width="12%"
                  marginLeft="2%"
                  verticalAlignment="center"
                  horizontalAlignment="center"
                  borderRadius="8vw"
                  borderColor="#492dc9de"
                  borderWidth="4"
                />
              {/if}
            </stackLayout>
          {/each}
        </stackLayout>
      </scrollView>
    </dockLayout>
  </page>
  
  <style>
    .action-Bar {
      height: 60;
      z-index: 400;
      transition: ease-in-out 0.4s
    }
  
    .topUp {
      /*animation: gotoTop ease-in-out 1s forwards;*/
    }
  @keyframes gotoDown {
      0% {
        transform: translateY(-100px);
        height: 60;
      }
      50% {
        transform: translateY(10px);
      }
      100% {
        transform: translateY(0px);
        height: 60;
      }
    }
    .topDefault {
      animation: gotoDown ease-in-out 1s forwards;
    }
  
    .bd-visible {
      animation: gotoDownBd ease-in-out 1s forwards;
    }
  
    .bd-closed {
      animation: gotoTopBd ease-in-out 1s forwards;
    }
  
    .custom-button {
      outline: none;
      border-style: none;
    }
  
    .dock-content {
      position: relative;
      overflow: auto;
    }
  
    .page-css {
      border-top: 6px solid #492dc9de;
      box-sizing: content-box;
    }
  
    .dock-bottom {
      transition: ease-in-out 0.4s;
    }
  
    .item {
      margin-top: 10vh;
      outline: 2px dashed red;
    }
  
    @keyframes fade-in-out {
      0% {
        opacity: 0;
      }
      100% {
        opacity: 1;
      }
    }
  
    @keyframes gotoTop {
      0% {
        transform: translateY(0px);
        height: 60;
      }
      50% {
        transform: translateY(10px);
      }
      100% {
        transform: translateY(-100px);
        height: 20;
      }
    }
  
  
  
    @keyframes gotoTopBd {
      0% {
        transform: translateY(0px);
        height: 60;
      }
      50% {
        transform: translateY(10px);
      }
      100% {
        transform: translateY(-100px);
        height: 0;
      }
    }
  
    @keyframes gotoDownBd {
      0% {
        transform: translateY(-100px);
        height: 60;
      }
      50% {
        transform: translateY(10px);
      }
      100% {
        transform: translateY(0px);
        height: 60;
      }
    }
  </style>
  