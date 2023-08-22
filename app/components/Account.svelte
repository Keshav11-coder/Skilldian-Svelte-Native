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
  borderTopColor="#492dc9de"
  borderTopWidth="6"
  backgroundColor={isDarkMode === 32 ? "#343434" : "#cfcfcf"}
>
  <actionBar
    flat="true"
    class="action-Bar {!navVisible ? 'topUp' : ''}"
    marginLeft="-20"
    backgroundColor={isDarkMode === 32 ? "#343434" : "#cfcfcf"}
  >
    <stackLayout orientation="horizontal">
      <button
        on:tap={() => pageSelector(0)}
        class="custom-button"
        width="36"
        height="36"
        backgroundImage="url('https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
        32
          ? 'back.png'
          : 'back_B.png'}')"
        backgroundSize="80% 80%"
        backgroundRepeat="no-repeat"
        backgroundPosition="center"
        marginRight="100%"
        backgroundColor="transparent"
      />
    </stackLayout>
  </actionBar>

  <dockLayout height="100%">
    <stackLayout orientation="vertical" dock="top">
      <stackLayout verticalAlignment="top" orientation="vertical">
        <stackLayout
          height="150vw"
          width="150vw"
          borderWidth="4px"
          borderColor="#492dc9de"
          borderRadius="100%"
          ><image
            borderRadius="100%"
            src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/ocd-f.jpg"
          /></stackLayout
        >
        <label
          text="Keshav Haripersad"
          fontSize="30"
          horizontalAlignment="center"
          marginTop="2%"
          opacity="0.85"
        />
      </stackLayout>
      <stackLayout
        orientation="vertical"
        height="10%"
        marginTop="2%"
        paddingLeft="20%"
        paddingRight="20%"
        backgroundColor="#2b2b2c"
        borderTopLeftRadius="18"
        borderTopRightRadius="18"
        width="94%"
      >
        <dockLayout
          orientation="horizontal"
          height="100%"
          borderBottomWidth="3px"
          borderColor="#bebebea4"
        >
          <image
            dock="right"
            width="25"
            height="25"
            src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
            32
              ? 'edit.png'
              : 'edit_B.png'}"
            opacity="0.8"
          />
          <label text="Edit Profile" fontSize="20" opacity="0.8" />
        </dockLayout>
      </stackLayout>
      <stackLayout
        orientation="vertical"
        height="10%"
        paddingLeft="20%"
        paddingRight="20%"
        backgroundColor="#2b2b2c"
        width="94%"
      >
        <dockLayout
          orientation="horizontal"
          height="100%"
          borderBottomWidth="3px"
          borderColor="#bebebea4"
        >
          <image
            dock="right"
            width="25"
            height="25"
            src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
            32
              ? 'profile.png'
              : 'profile_B.png'}"
            opacity="0.8"
          />
          <label text="Account Settings" fontSize="20" opacity="0.8" />
        </dockLayout>
      </stackLayout>
      <stackLayout
        orientation="vertical"
        height="10%"
        paddingLeft="20%"
        paddingRight="20%"
        backgroundColor="#2b2b2c"
        borderBottomLeftRadius="18"
        borderBottomRightRadius="18"
        width="94%"
      >
        <dockLayout orientation="horizontal" height="100%">
          <image
            dock="right"
            width="25"
            height="25"
            src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/{isDarkMode ===
            32
              ? 'settings.png'
              : 'settings_B.png'}"
            opacity="0.8"
          />
          <label text="App Settings" fontSize="20" opacity="0.8" />
        </dockLayout>
      </stackLayout>
    </stackLayout>

    <dockLayout height="70" orientation="horizontal" dock="bottom" verticalAlignment="bottom">
      <stacklayout marginLeft="2%" width="60" height="50"><image width="80%" hegiht="80%" borderRadius="10%" src="https://raw.githubusercontent.com/Keshav11-coder/Snadian/main/Sdn-native-im/skilldian.png"></image></stacklayout>
      <label text="Skilldian" fontSize="20"></label>
      <label text="sign up" textAlignment="center" width="64" height="32" fontSize="15" backgroundColor="#492dc9de" borderWidth="2px" borderColor="white" horizontalAlignment="right" borderRadius="20%" marginRight="2%"></label>
    </dockLayout>
  </dockLayout>
</page>

<style>
  .li01 {
    position: absolute;
    left: 0;
    right: 0;
    height: 2px;
    background-color: #bebebea4; /* Adjust the color as desired */
  }
</style>
