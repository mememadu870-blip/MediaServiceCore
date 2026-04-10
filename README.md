# MediaServiceCore

SmartTube 媒体服务核心库 - OkHttp 4.x API 修复

## 修复内容

### OkHttp 4.x API 兼容性修复

升级到 OkHttp 4.10.0 后，修复了以下 API 变更：

1. **MediaType.parse() → String.toMediaType()**
   - 文件：`youtubeapi/src/main/java/com/liskovsoft/googleapi/drive3/DriveServiceInt.kt`
   - 原因：OkHttp 4.x 使用 Kotlin 扩展函数

2. **RequestBody.create() → String.toRequestBody() / ByteArray.toRequestBody()**
   - 文件：`youtubeapi/src/main/java/com/liskovsoft/googleapi/drive3/DriveServiceInt.kt`
   - 原因：OkHttp 4.x 使用扩展函数创建 RequestBody

3. **属性访问变更（方法 → 属性）**
   - 文件：`youtubeapi/src/main/java/com/liskovsoft/googlecommon/common/helpers/RetrofitOkHttpHelper.kt`
   - `request.headers()` → `request.headers`
   - `request.url()` → `request.url`

4. **Response 属性访问变更**
   - 文件：`youtubeapi/src/main/java/com/liskovsoft/youtubeapi/app/nsigsolver/common/InfoExtractor.kt`
   - 文件：`youtubeapi/src/main/java/com/liskovsoft/youtubeapi/app/potokennp2/PoTokenWebView.kt`
   - `response.body()` → `response.body`
   - `response.code()` → `response.code`

### Kotlin 编译配置

添加 `kotlinOptions { jvmTarget = '1.8' }` 以支持 Gradle 7.5 + JDK17

## 依赖版本

```gradle
okhttpVersion = '4.10.0'  // 支持 Coil 2.x
```

## 构建说明

```bash
# 环境要求
- JDK 17
- Gradle 7.5
- Android SDK 34

# 编译
./gradlew build
```

## 使用方式

作为子模块使用：

```bash
git submodule add https://github.com/mememadu870-blip/MediaServiceCore.git MediaServiceCore
```

## 变更历史

### 2026-04-08
- 升级 OkHttp 到 4.10.0
- 修复 DriveServiceInt.kt 中的 MediaType 和 RequestBody API
- 修复 RetrofitOkHttpHelper.kt 中的 Headers 和 HttpUrl 访问
- 修复 InfoExtractor.kt 和 PoTokenWebView.kt 中的 Response 访问
- 添加 Kotlin jvmTarget 配置

## 原始项目

基于 https://github.com/yuliskov/MediaServiceCore 修改
