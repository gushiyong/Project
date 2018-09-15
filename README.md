<h1>常用命令</h1>
	打开重新加载框：adb shell input keyevent 82
<h1>在线模拟器</h1>
	http://dabbott.github.io/react-native-web-player/
<h1>React-native-swiper的使用</h1>
	使用说明： 
	1. 先安装React-native-swiper 
	npm i react-native-swiper –save 
	2. 导入Swiper 
	import Swiper from ‘react-native-swiper’;
    安装插件命令：npm install xxxxxxx –-save 

<h1>RefreshControl的使用</h1>
	使用说明： 
	<RefreshControl
	      refreshing={this.state.isRefreshing}
	      onRefresh={this._onRefresh.bind(this)}
	      colors={['#ddd', '#0398ff']}
	      progressBackgroundColor="#ffffff"/>

<h1>react-native打离线bundle包</h1>
     1.在工程根目录下执行打包命令:	react-native bundle --entry-file index.android.js --bundle-output ./android/app/src/main/assets/index.android.jsbundle --platform android --assets-dest ./android/app/src/main/res/ --dev false   注意:[./android/app/src/main/	assets/]文件夹存在。
     2.增量升级的话不要把图片资源直接打包到res中，脚本如下： 
	   react-native bundle --entry-file index.js --bundle-output ./bundle/androidBundle/index.android.jsbundle --platform android --assets-dest ./bundle/androidBundle/ --dev false
	 3.保证MainActivity.Java中的setBundleAssetName与你的jsbundle文件名一致，比如.setBundleAssetName(“index.android.jsbundle”)就与我生成的资源名一致
<h1>加载离线jsBundle包</h1>
        mReactRootView = (ReactRootView) findViewById(R.id.test_js);
        ReactInstanceManager mReactInstanceManager = ReactInstanceManager.builder()
                .setApplication(getApplication())
                .setBundleAssetName("index.android.jsbundle")
			//  .setJSMainModuleName("android")
                .addPackage(new MainReactPackage())
                .setUseDeveloperSupport(BuildConfig.DEBUG)
                .setInitialLifecycleState(LifecycleState.RESUMED)
                .build();
        mReactRootView.startReactApplication(mReactInstanceManager, "Test", null);


##<h1>React-Native遇到的问题</h1>
**1、undefined is not an object (evaluating '_reactNative.PropTypes.string') Error**

	解决办法：import PropTypes from 'prop-types';
	网址：https://stackoverflow.com/questions/37746451/undefined-is-not-an-object-evaluating-reactnative-proptypes-string-error

**2、ReferenceError cant find variable:View**
	
	可能的原因是没有导入包  例如：import{ View } from 'react-native';

**3、Warning:isMounted(...) is deprecated in plain JavaScript React classes**
	
	FaceBook的Bug,目前处理办法是忽略警告：import { YellowBox } from 'react-native';YellowBox.
	ignoreWarnings(['Warning: isMounted(...) is deprecated', 'Module RCTImageLoader']);

**4、TypeError: Cannot read property xxx of undefined**
	
	添加非空判断 例：  if (json) {
			            this.setState({
			                movies: this.state.movies.concat(json.subjects),
			            });
			        }
**5、Error: EPERM: operation not permitted, rename 'D:\WebstormProjects\Test\node_modules\.staging\react-native-	swiper-785a4889' -> 'D:\WebstormProjects\Test\node_modules\react-native-swiper'**
	
	处理办法：可能是文件读写权限问题，打开所有权限即可.![](https://i.imgur.com/6ohlqgS.png)

**6、Could not expand ZIP 'C:\Users\Administrator\.gradle\caches\modules-2\files-2.1\com.facebook.fresco\drawee	\1.3.0\c88fb84ed4ae8a4e0efe6fd3cad1a1d20c19ea69\drawee-1.3.0.aar'.**
	
	处理办法：cd android && gradlew clean && cd .. && react-native run-android

##<h1>Android日常开发遇到的问题</h1>
**1、ListView 中嵌套GridView include或者Item布局 中高度需要设置成match_parent**


	


