# 智慧海洋牧场可视化系统 (Smart Ocean Ranch Visualization System)

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Flask](https://img.shields.io/badge/flask-2.0+-green.svg)](https://flask.palletsprojects.com/)

2025春 软件工程课程项目 - 智慧海洋牧场系统

## 📋 项目简介

智慧海洋牧场可视化系统是一个基于Web的综合管理平台，旨在为海洋养殖场提供智能化的监控、分析和决策支持。系统集成了实时监控、数据可视化、AI智能分析等功能，帮助养殖场管理者更好地管理养殖资源和优化生产决策。

## ✨ 主要功能

### 🎯 核心功能
- **用户认证系统**: 支持用户注册、登录，区分普通用户和管理员权限
- **实时监控看板**: 实时显示养殖场各项关键指标
- **数据可视化**: 支持JSON和CSV数据的图表化展示
- **水质监测**: 实时监控水温、pH、溶解氧、氨氮等9项水质指标
- **鱼类信息管理**: 记录和分析鱼类种类、体重、体长等数据

### 🤖 智能功能
- **AI智能问答**: 基于Kimi API的智能对话系统，提供养殖咨询服务
- **图像识别**: 上传图片进行鱼类识别和分析
- **体长预测**: 基于机器学习模型预测鱼类体长
- **养殖趋势分析**: 分析历史数据，预测养殖趋势
- **风险评估**: 评估养殖过程中的潜在风险
- **决策支持**: 基于数据分析提供智能决策建议

### 📊 数据管理
- **数据中心**: 集中管理各类养殖数据
- **传感器管理**: 管理各类传感器设备和数据采集
- **数据导入导出**: 支持批量数据导入和报表导出

## 🛠 技术栈

### 后端技术
- **Python 3.8+**: 主要编程语言
- **Flask**: Web框架
- **MySQL**: 关系型数据库
- **PyMySQL/mysql-connector-python**: MySQL数据库连接器

### 前端技术
- **HTML5/CSS3**: 页面结构和样式
- **JavaScript**: 交互逻辑
- **Chart.js/ECharts**: 数据可视化图表库（推测）

### AI/ML技术
- **OpenAI API (Kimi)**: 智能问答和图像识别
- **scikit-learn**: 机器学习模型训练和预测
- **pickle**: 模型序列化

### 开发工具
- **Git**: 版本控制
- **python-dotenv**: 环境变量管理

## 📦 系统要求

- **操作系统**: Windows/Linux/macOS
- **Python**: 3.8 或更高版本
- **MySQL**: 5.7 或更高版本
- **浏览器**: Chrome/Firefox/Safari/Edge (最新版本)
- **内存**: 建议 4GB 以上
- **硬盘**: 至少 1GB 可用空间

## 🚀 快速开始

### 1. 克隆项目

```bash
git clone https://github.com/MengQxuan/software-engineering.git
cd software-engineering/Software-Engineering-main
```

### 2. 安装Python依赖

```bash
# 推荐使用虚拟环境
python -m venv venv

# 激活虚拟环境
# Windows:
venv\Scripts\activate
# Linux/macOS:
source venv/bin/activate

# 安装依赖（主要依赖）
pip install flask
pip install pymysql
pip install mysql-connector-python
pip install openai
pip install python-dotenv
pip install scikit-learn
pip install pandas
pip install numpy
```

### 3. 配置数据库

#### 3.1 安装MySQL
确保MySQL已安装并运行。

#### 3.2 创建数据库
```bash
# 登录MySQL
mysql -u root -p

# 在MySQL命令行中执行
source /path/to/database_setup/setup_database.sql
```

**注意**: 将 `/path/to/` 替换为实际的项目路径。

#### 3.3 配置数据库连接
编辑 `config.py` 文件，修改数据库连接信息：

```python
DB_CONFIG = {
    "host": "localhost",
    "user": "root",
    "password": "your_password",  # 修改为你的MySQL密码
    "database": "smart_ocean_ranch"
}
```

### 4. 配置API密钥

编辑 `app/Kimi/.env` 文件，添加你的Kimi API密钥：

```env
MOONSHOT_API_KEY=your_api_key_here
```

**获取API密钥**: 访问 [Kimi开放平台](https://platform.moonshot.cn/) 申请API密钥。

**安全提示**: 不要将API密钥提交到版本控制系统！确保 `.env` 文件在 `.gitignore` 中。

### 5. 初始化数据（可选）

```bash
cd database_setup

# 导入水质数据
python water_data.py

# 导入鱼类数据
python fish_data.py

# 创建示例数据
python create_data.py
```

### 6. 运行应用

```bash
# 返回项目根目录
cd ..

# 启动应用
python run.py
```

应用将在 `http://localhost:5000` 启动。

### 7. 访问系统

在浏览器中打开 `http://localhost:5000`，即可访问系统。

**默认账户**（如果有初始化数据）:
- 管理员账户: 请查看数据库或联系项目维护者
- 普通用户: 可通过注册页面创建新账户

## 📁 项目结构

```
software-engineering/
├── Software-Engineering-main/          # 主项目目录
│   ├── app/                           # 应用主目录
│   │   ├── __init__.py               # Flask应用初始化
│   │   ├── routes/                   # 路由蓝图
│   │   │   ├── auth.py              # 认证路由（登录/注册）
│   │   │   ├── main.py              # 主页路由
│   │   │   ├── admin.py             # 管理员路由
│   │   │   ├── info.py              # 信息展示路由
│   │   │   ├── underwater.py        # 水下系统路由
│   │   │   ├── smartcenter.py       # 智能中心路由
│   │   │   ├── datacenter.py        # 数据中心路由
│   │   │   └── trend.py             # 趋势分析路由
│   │   ├── templates/                # HTML模板
│   │   │   ├── index.html           # 登录页面
│   │   │   ├── main.html            # 主页面
│   │   │   ├── dashboard.html       # 仪表盘
│   │   │   ├── smartcenter.html     # 智能中心
│   │   │   ├── chat.html            # AI聊天
│   │   │   ├── image.html           # 图像识别
│   │   │   ├── length_predict.html  # 体长预测
│   │   │   └── ...                  # 其他页面
│   │   ├── static/                   # 静态资源（CSS/JS/图片）
│   │   ├── Kimi/                     # AI功能模块
│   │   │   ├── chat.py              # 智能问答
│   │   │   ├── image.py             # 图像识别
│   │   │   ├── train.py             # 模型训练和预测
│   │   │   ├── .env                 # API密钥配置
│   │   │   ├── fish_model.pkl       # 预训练模型
│   │   │   └── fish_encoder.pkl     # 特征编码器
│   │   ├── visualization/            # 可视化模块
│   │   │   ├── json_visualizer.py   # JSON可视化
│   │   │   └── csv_visualizer.py    # CSV可视化
│   │   └── upload/                   # 文件上传目录
│   ├── database_setup/               # 数据库配置
│   │   ├── setup_database.sql       # 数据库初始化脚本
│   │   ├── water_data.py            # 水质数据导入
│   │   ├── fish_data.py             # 鱼类数据导入
│   │   └── create_data.py           # 示例数据生成
│   ├── data/                         # 数据文件
│   │   ├── Fish.csv                 # 鱼类数据
│   │   ├── water/                   # 水质数据
│   │   ├── 数据说明.md              # 数据说明文档
│   │   └── 水质评价指标.png          # 水质评价标准
│   ├── config.py                     # 配置文件
│   ├── run.py                        # 应用启动文件
│   └── README.md                     # 项目说明文档
├── 演示视频.mp4                       # 项目演示视频
├── 软件开发文档.pdf                   # 软件开发文档
├── 2212452-孟启轩-软件设计.pdf        # 软件设计文档
├── 2212452-孟启轩-软件调研.pdf        # 软件调研文档
├── 2212452-孟启轩-需求分析.pdf        # 需求分析文档
├── 2212452-孟启轩-项目管理.pdf        # 项目管理文档
└── README.md                         # 本文档

```

## 🔧 配置说明

### 数据库配置 (config.py)

```python
DB_CONFIG = {
    "host": "localhost",      # 数据库主机地址
    "user": "root",           # 数据库用户名
    "password": "password",   # 数据库密码（请修改）
    "database": "smart_ocean_ranch"  # 数据库名称
}
```

### API配置 (app/Kimi/.env)

```env
MOONSHOT_API_KEY=your_moonshot_api_key
```

### 应用配置 (run.py)

```python
app.run(
    host='0.0.0.0',  # 监听所有网络接口
    port=5000,        # 端口号
    debug=True        # 调试模式（生产环境请设为False）
)
```

## 📚 API接口文档

### 认证相关 (/auth)
- `POST /login` - 用户登录
- `POST /register` - 用户注册
- `GET /logout` - 用户登出

### 智能中心 (/smartcenter)
- `GET /smartcenter` - 智能中心主页
- `POST /predict` - 体长预测
- `POST /chat` - AI问答
- `POST /image_recognition` - 图像识别

### 信息查询 (/info)
- `GET /getweight` - 获取鱼类重量数据
- `GET /get_species` - 获取鱼类种类统计
- `GET /info` - 信息总览页面

### 数据中心 (/datacenter)
- `GET /datacenter` - 数据中心主页
- `GET /sensor_data` - 获取传感器数据
- `GET /water_quality` - 获取水质数据

### 可视化
- `GET /visualize/json` - JSON数据可视化
- `GET /visualize/csv` - CSV数据可视化

## 🎨 使用示例

### 1. 体长预测

```javascript
// 前端调用示例
fetch('/predict', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({
        species: 'Perch',
        length1: 25.5,
        length2: 28.0
    })
})
.then(response => response.json())
.then(data => console.log(data));
```

### 2. AI问答

```javascript
// AI聊天示例
fetch('/chat', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({
        message: '如何提高鱼类养殖效率？'
    })
})
.then(response => response.json())
.then(data => console.log(data.response));
```

## 📝 数据说明

### 水质数据
系统监测9项水质指标：
- 水温 (Temperature)
- pH值
- 溶解氧 (Dissolved Oxygen)
- 电导率 (Conductivity)
- 浊度 (Turbidity)
- 高锰酸盐指数
- 氨氮 (Ammonia Nitrogen)
- 总磷 (Total Phosphorus)
- 总氮 (Total Nitrogen)

数据来源：中国环境监测总站
评价标准：《地表水环境质量标准(GB3838-2002)》

### 鱼类数据
包含以下字段：
- `species`: 种类
- `weight`: 体重 (克)
- `length1`: 体长-1 (厘米)
- `length2`: 体长-2 (厘米)
- `height`: 高度（背部到腹部的垂直距离）
- `width`: 宽度（鱼体中段的最大宽度）

更多信息请参考: [Fish4Knowledge数据集](https://homepages.inf.ed.ac.uk/rbf/fish4knowledge/)

## 🔒 安全注意事项

1. **修改默认密码**: 首次部署后立即修改数据库默认密码
2. **保护API密钥**: 不要将 `.env` 文件提交到版本控制
3. **生产环境配置**: 
   - 关闭Flask的debug模式
   - 使用强密码
   - 配置HTTPS
   - 使用环境变量管理敏感信息
4. **数据备份**: 定期备份数据库
5. **输入验证**: 系统已实现基本的输入验证，但在生产环境中建议加强

## 🐛 常见问题

### Q: 启动时提示端口被占用
**A**: 修改 `run.py` 中的端口号，或者关闭占用5000端口的其他程序。

### Q: 数据库连接失败
**A**: 
1. 确认MySQL服务已启动
2. 检查 `config.py` 中的数据库配置
3. 确认数据库 `smart_ocean_ranch` 已创建

### Q: 页面跳转出现404错误
**A**: 检查路由是否在 `app/__init__.py` 中注册了相应的蓝图。

### Q: AI功能无法使用
**A**: 
1. 检查 `app/Kimi/.env` 文件中的API密钥配置
2. 确认网络连接正常
3. 检查API密钥是否有效且有足够的配额

### Q: 模型预测出错
**A**: 
1. 确认 `app/Kimi/fish_model.pkl` 和 `fish_encoder.pkl` 文件存在
2. 检查输入数据格式是否正确
3. 查看控制台日志了解详细错误信息

## 🚧 开发计划

- [ ] 添加更多数据可视化图表类型
- [ ] 实现实时数据推送（WebSocket）
- [ ] 添加移动端适配
- [ ] 增强权限管理系统
- [ ] 添加数据导出功能
- [ ] 实现多语言支持
- [ ] 添加单元测试和集成测试
- [ ] 性能优化和缓存机制

## 👥 贡献指南

欢迎贡献代码！请遵循以下步骤：

1. Fork本项目
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启Pull Request

### 代码规范
- 遵循PEP 8 Python代码规范
- 添加必要的注释
- 保持代码简洁清晰
- 提交前进行测试

## 📄 许可证

本项目为课程作业项目。具体许可证信息请联系项目作者。

## 📞 联系方式

- **项目作者**: 孟启轩 (学号: 2212452)
- **GitHub**: [MengQxuan](https://github.com/MengQxuan)
- **项目仓库**: [software-engineering](https://github.com/MengQxuan/software-engineering)

## 🙏 致谢

- 感谢所有为本项目提供数据和支持的组织机构
- 感谢开源社区提供的优秀框架和工具
- 特别感谢课程指导老师的悉心指导

## 📚 相关文档

- [演示视频](./演示视频.mp4)
- [软件开发文档](./软件开发文档.pdf)
- [软件设计文档](./2212452-孟启轩-软件设计.pdf)
- [软件调研文档](./2212452-孟启轩-软件调研.pdf)
- [需求分析文档](./2212452-孟启轩-需求分析.pdf)
- [项目管理文档](./2212452-孟启轩-项目管理.pdf)
- [数据说明](./Software-Engineering-main/data/数据说明.md)

---

**注意**: 本项目为教学项目，部分功能可能需要根据实际需求进行调整和完善。建议在生产环境部署前进行全面的安全审查和性能测试。