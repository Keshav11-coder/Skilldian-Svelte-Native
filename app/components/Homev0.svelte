<script>
  import {
    Application,
    querySelectorAll,
    widthProperty,
  } from "@nativescript/core";

  const isDarkMode =
    Application.android?.context?.getResources().getConfiguration().uiMode &
    android.content.res.Configuration.UI_MODE_NIGHT_MASK;

    function handleScroll(args) {
    const scrollView = args.object;
    const currentScrollPosition = scrollView.verticalOffset;

    if (currentScrollPosition > previousScrollPosition) {
      console.log("Scrolling down");
    } else if (currentScrollPosition < previousScrollPosition) {
      console.log("Scrolling up");
    }

    previousScrollPosition = currentScrollPosition;
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

<page class="page-css">
  <actionBar class="action-Bar" flat="true" marginLeft="-10" marginTop="6">
    <stackLayout orientation="horizontal">
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
    </stackLayout>
  </actionBar>
  <scrollView orientation="vertical" on:scroll={() => handleScroll(this)}>
    <stackLayout
      on:scroll={handleScroll}
      padding="10"
      backgroundColor={isDarkMode === 32 ? "#343434" : "#cfcfcf"}
      orientation="vertical"
    >

      {#each items as item}
        <stackLayout
          orientation="horizontal"
          width="100%"
          height={item.type === "premium" ? "140vw" : "90vw"}
          class="item"
        >
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
            src="/app/images/search.png"
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
              class=""
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
</page>

<style>
  .action-Bar {
    margin-left: 0;
  }

  .custom-button {
    outline: none;
    border-style: none;
  }

  .page-css {
    background-color: #492dc9de;
  }

  .item {
    margin-top: 10vh;
  }

  .description {
    width: 100%;
    height: 60%;
    background-color: purple;
  }

  @keyframes fade-in-out {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
</style>
