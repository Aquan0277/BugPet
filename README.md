[README.md](https://github.com/user-attachments/files/26440702/README.md)
# BugPet - 习惯养成宠物App

## 项目结构

```
BugPet/
├── app/
│   ├── build.gradle.kts
│   ├── proguard-rules.pro
│   └── src/main/
│       ├── AndroidManifest.xml
│       ├── java/com/bugpet/app/
│       │   ├── BugPetApplication.kt       # Application入口，Hilt初始化
│       │   ├── MainActivity.kt            # 主Activity，底部导航
│       │   ├── data/
│       │   │   ├── model/
│       │   │   │   ├── Habit.kt           # 习惯数据模型
│       │   │   │   ├── HabitRecord.kt     # 打卡记录模型
│       │   │   │   └── Pet.kt             # 宠物模型+阶段枚举
│       │   │   ├── db/
│       │   │   │   ├── BugPetDatabase.kt  # Room数据库
│       │   │   │   ├── HabitDao.kt        # 习惯数据访问
│       │   │   │   └── PetDao.kt          # 宠物数据访问
│       │   │   └── repository/
│       │   │       ├── HabitRepository.kt # 习惯业务逻辑
│       │   │       └── PetRepository.kt   # 宠物业务逻辑
│       │   ├── di/
│       │   │   └── DatabaseModule.kt      # Hilt依赖注入
│       │   ├── ui/
│       │   │   ├── navigation/
│       │   │   │   ├── Screen.kt          # 路由定义
│       │   │   │   └── BugPetNavHost.kt   # 导航图
│       │   │   ├── screens/
│       │   │   │   ├── HomeScreen.kt      # 习惯列表+打卡
│       │   │   │   ├── AddHabitScreen.kt  # 添加习惯
│       │   │   │   ├── PetScreen.kt       # 宠物展示
│       │   │   │   └── StatsScreen.kt     # 统计页
│       │   │   ├── theme/
│       │   │   │   └── Theme.kt           # Material3主题
│       │   │   └── viewmodel/
│       │   │       ├── HabitViewModel.kt  # 习惯状态管理
│       │   │       └── PetViewModel.kt    # 宠物状态管理
│       │   └── worker/
│       │       ├── BootReceiver.kt        # 开机启动WorkManager
│       │       └── ReminderWorker.kt      # 每日提醒通知
│       └── res/
│           ├── drawable/
│           │   └── ic_pet_notification.xml
│           └── values/
│               ├── strings.xml
│               └── themes.xml
├── gradle/
│   └── libs.versions.toml             # 依赖版本管理
├── build.gradle.kts
├── settings.gradle.kts
└── gradle.properties
```

---

## 快速开始

### 第一步：安装Android Studio
1. 下载 Android Studio Ladybug（或更新版本）
2. 安装时勾选 Android SDK、Android Virtual Device
3. 首次启动后下载 SDK（API 35）

### 第二步：打开项目
1. 打开 Android Studio
2. 选择 **Open** → 选择 `D:\Claude\BugPet` 文件夹
3. 等待 Gradle 同步完成（首次约5-15分钟，需要下载依赖）

### 第三步：运行App
- **模拟器**：点击 Device Manager → Create Virtual Device → Pixel 8 → API 35
- **真机**：手机开启「开发者选项」→「USB调试」，插线后点击 ▶ 运行

---

## 功能说明

| 功能 | 说明 |
|------|------|
| 习惯列表 | 展示所有习惯，点击圆圈打卡，支持删除 |
| 添加习惯 | 设置名称、图标emoji、每日/每周频率 |
| 宠物页面 | 查看宠物当前阶段（蛋→幼虫→茧→蝴蝶→龙） |
| 统计页面 | 今日完成数、各习惯连续天数 |
| 每日提醒 | 自动推送通知提醒打卡 |

## 宠物成长规则
- 每完成1次习惯打卡 → 获得1点能量
- 能量满10点 → 宠物升级
- Lv.1: 🥚蛋 → Lv.2-3: 🐛幼虫 → Lv.4-5: 🫘茧 → Lv.6-9: 🦋蝴蝶 → Lv.10+: 🐉龙

---

## 后续云服务器接入计划

当本地版本稳定后，接入以下后端能力：
1. **用户账号**：Firebase Auth 或自建JWT登录
2. **数据同步**：本地Room数据 ↔ 云端数据库（PostgreSQL/Supabase）
3. **API层**：Ktor（Kotlin）或 FastAPI（Python）后端
4. **推送升级**：FCM（Firebase Cloud Messaging）替代本地通知
5. **排行榜**：好友间习惯PK功能

告知老板需要哪个方向，小弟继续搭建。
