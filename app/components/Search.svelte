<script>
  let isDarkMode = 32;
  let navVisible = "true";

  export let page;

  function pageSelector(index) {
    page = index;
    console.log(page);
  }
</script>

<page
  class="page-css"
  borderTopColor="#3b2e98de"
  borderTopWidth="6"
  backgroundColor={isDarkMode === 32 ? "#2b2726" : "#cfcfcf"}
>
  <actionBar
    flat="true"
    class="action-Bar {!navVisible ? 'topUp' : ''}"
    backgroundColor="#2f2c2a"
    width="70%"
    height="65"
  >
    <stackLayout orientation="horizontal" marginTop="5">
      <button
        on:tap={() => pageSelector(0)}
        width="30"
        height="30"
        margin="0"
        backgroundImage="url('https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
        32
          ? 'back.png'
          : 'back_B.png'}')"
        backgroundSize="90% 90%"
        backgroundRepeat="no-repeat"
        backgroundPosition="center"
        backgroundColor="transparent"
      />
      <textField
        horizontalAlignment="center"
        hint="search here..."
        editable="true"
        width="70%"
        height="75%"
        paddingLeft="10"
        fontSize="18"
        backgroundColor="#ffffff47"
        borderRadius="5vw"
        borderBottomColor="transparent"
        style="placeholder-color:white"
      />
      <button
        on:tap={() => pageSelector(0)}
        width="30"
        height="30"
        margin="0"
        backgroundImage="url('https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
        32
          ? 'search.png'
          : 'search_B.png'}')"
        backgroundSize="80% 80%"
        backgroundRepeat="no-repeat"
        backgroundPosition="center"
        backgroundColor="transparent"
      />
    </stackLayout>
  </actionBar>

  <dockLayout class="dock-content" verticalAlignment="top" height="100%">
    <stackLayout
      orientation="horizontal"
      height="50"
      dock="bottom"
      backgroundColor="#2f2c2a"
      class={navVisible ? "bnavShow" : "bnavHide"}
    >
      <absoluteLayout
        width="12%"
        height="50%"
        marginLeft="7%"
        marginRight="3.3%"
      >
        <button
          backgroundColor="transparent"
          width="100%"
          height="100%"
          boxShadow="none"
        />
        <image
          width="100%"
          height="100%"
          src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
          32
            ? 'home.png'
            : 'home_B.png'}"
        />
      </absoluteLayout>
      <absoluteLayout
        width="12%"
        height="50%"
        marginLeft="3.3%"
        marginRight="3.3%"
        paddingTop="2"
        paddingLeft="7"
      >
        <button
          backgroundColor="transparent"
          width="80%"
          height="80%"
          boxShadow="none"
        />
        <image
          width="85%"
          height="85%"
          src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
          32
            ? 'posts.png'
            : 'posts_B.png'}"
        />
      </absoluteLayout>
      <absoluteLayout
        width="12%"
        height="50%"
        marginLeft="3.3%"
        marginRight="3.3%"
      >
        <button
          backgroundColor="transparent"
          width="100%"
          height="100%"
          boxShadow="none"
        />
        <image
          width="105%"
          height="105%"
          src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
          32
            ? 'bookmark.png'
            : 'bookmark_B.png'}"
        />
      </absoluteLayout>
      <absoluteLayout
        width="12%"
        height="50%"
        marginLeft="3.3%"
        marginRight="3.3%"
      >
        <button
          backgroundColor="transparent"
          width="100%"
          height="100%"
          boxShadow="none"
        />
        <image
          width="95%"
          height="95%"
          src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
          32
            ? 'post.png'
            : 'post_B.png'}"
          rotate="45"
        />
      </absoluteLayout>
      <absoluteLayout
        width="12%"
        height="50%"
        marginLeft="3.3%"
        marginRight="7%"
        paddingTop="2"
      >
        <button
          backgroundColor="transparent"
          width="100%"
          height="100%"
          boxShadow="none"
        />
        <image
          width="85%"
          height="85%"
          src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
          32
            ? 'bell.png'
            : 'bell_B.png'}"
        />
      </absoluteLayout>
    </stackLayout>
    <!--
        home - job main page
        posts - job posts, user posts
        bookmarks - job bookmarks, posts, .. mtc
        new post - create a new post / more
        notifications - new / history notifications
      -->
      <stackLayout dock="bottom" width="100%" height="100%">

      </stackLayout>
  </dockLayout>
</page>

<style>
</style>
