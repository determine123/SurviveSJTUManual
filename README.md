# README

&lt;上海交通大学生存手册&gt;于08年由一群交大本科生写就，12年过去了无数交大学子受益于它，但有些内容可能已经过时，由于原作者团队主要属于出国攻读博士群体，本手册在国内深造、国内就业等方面存在欠缺。本项目旨在将它制作成gitbook发布，并长期维护该项目，希望能给未来的交大在读和入学新生同学带来微小的帮助，尤其感谢本书原版的作者们！

暂定修改和增添内容如下:

* [x] 增加新版序言和声明
* [x] 更新留沪政策
* [x] 添加详细的本科生科研建议，以及选择导师的经验
* [x] 添加转专业经验章节进入立志篇部分
* [ ] 添加本科转学海外经验章节进入立志篇部分
* [ ] 添加交大各个专业的介绍进入生存技巧部分（该部分将在收集到足够投稿后按专业整合）
* [ ] 增加交大毕业生选调的经验介绍
* [ ] 增加保研、直博的经验介绍

以下内容将独立到[SJTU-Application](https://github.com/SurviveSJTU/SJTU-Application)，欢迎大家PR投稿，GitHub Page相比Gitbook更方便添加新内容。

* [ ] 采访各专业交大毕业生在读博士生和已毕业博士学长学姐们的经历和建议
* [ ] 更新保研政策与经验分享
* [ ] 由于目前就业大环境下滑，越来越多的同学选择了考研，我们希望收集一些考研成功的同学经验分享
* [ ] 添加本科去境外高校学期交换的经验分享
* [ ] 添加出国申请ms/phd以及暑期科研的经验风险

欢迎交大在读与已经毕业的同学提PR，也欢迎外校同学就实习、转学等项PR，如果您对本书内容有任何问题、或建议，请提issue，谢谢！

## 提 issue

如果对访谈集中的内容持有不同意见，或认为某段表述片面、不属实、已经过时，请先搜索已有 issue，再到 [issue 区](https://github.com/SurviveSJTU/SurviveSJTUManual/issues)提出。建议包含：

- 对应章节的链接和具体段落；
- 问题所在，以及适用的时间、专业或个人背景；
- 可核查的来源或个人经历，并区分事实与观点；
- 建议如何修改。

我们会尽力寻找相似背景的同学进行二次 review，再决定如何修改。也欢迎提交内容补充、错别字和失效链接等问题。

## 环境要求

- **网页编辑与提 PR**：只需要 GitHub 账号和浏览器，无需安装 Git、Node.js 或 GitBook，也不需要注册 GitBook 账号。
- **本地编辑与提 PR**：需要 Git 和文本编辑器；文档采用 Markdown，最新版目录为 [SUMMARY.md](SUMMARY.md)。
- **可选的本地电子书构建**：当前[发布工作流](.github/workflows/continuous-release.yml)使用 Ubuntu、Node.js 24 / npm、HonKit、Calibre、GNU awk 和 Noto 中文字体。这些工具只用于生成 EPUB / PDF，不是参与文字贡献的前提。

## 如何提 PR

### 方式一：直接在 GitHub 网页编辑

1. 登录 GitHub，在本仓库打开需要修改的 Markdown 文件，点击编辑按钮；没有写权限时，按页面提示 fork 到个人账户。
2. 修改内容，并使用 Preview 检查 Markdown 排版。如果新增章节，请同时在 `SUMMARY.md` 中添加链接。
3. 提交到个人 fork 的工作分支，按页面提示创建 PR。确认目标仓库为 `SurviveSJTU/SurviveSJTUManual`、目标分支为 `master`。
4. 在 PR 中说明改了什么、为什么修改，以及相关来源或 issue。等待维护者 review，按反馈继续修改；审核通过后由维护者合并到 `master`。

### 方式二：在本地使用 Git

先在 GitHub 点击 Fork，再运行以下命令，将 `YOUR_USERNAME` 替换为自己的用户名：

```sh
git clone https://github.com/YOUR_USERNAME/SurviveSJTUManual.git
cd SurviveSJTUManual
git remote add upstream https://github.com/SurviveSJTU/SurviveSJTUManual.git
git fetch upstream
git switch -c docs/my-update upstream/master
```

编辑相关 Markdown 文件及目录后，检查并提交改动：

```sh
git diff --check
git diff
git add README.md
git commit -m "docs: update contribution instructions"
git push -u origin docs/my-update
```

这里以修改 `README.md` 为例；请将 `git add` 的文件名和提交说明替换为本次实际修改的内容。随后在 GitHub 个人 fork 中创建 PR，目标仓库和分支同上。使用 GitBook 编辑也是可选方式，但无需为了提交 PR 专门使用 GitBook。

提交前请检查段落、链接和目录入口；经验分享应注明背景和时间，政策信息应附对应的官方来源，避免提交他人的隐私或未获许可的材料。

### 可选：本地生成 EPUB / PDF

如需复现当前发布流程，建议使用 Ubuntu；Windows 用户可以使用 Ubuntu WSL。先安装 Node.js 24 和 npm，再安装构建依赖。以下命令与仓库的 Ubuntu 发布工作流对应：

```sh
sudo apt update
sudo apt install -y calibre gawk fonts-noto-cjk-extra fonts-noto-mono
npm install -g honkit
bash .github/resources/build-ebooks.sh
```

构建成功后，仓库根目录会生成 `SurviveSJTUManual.epub` 和 `SurviveSJTUManual.pdf`。其他系统的安装方式可参考 [HonKit 文档](https://honkit.netlify.app/setup.html)及 [Calibre 下载页](https://calibre-ebook.com/download)。

构建脚本会临时修改根目录的 `README.md`，并在正常结束时恢复。请在工作区干净时执行；若构建中断，先检查 `git diff`，从脚本创建的临时备份恢复文件，避免误提交构建产生的修改。电子书构建输出无需随文字 PR 提交。

## 旧版目录（最新版请参考SUMMARY.md）

<!--
workaround:
- try preventing the old TOC from being reading by ebook builders, otherwise wrong links will be generated.
- try preventing the old TOC from being reading by readers.
-->
<details>
<summary>旧版目录</summary>

### 序

* [声明](xu/sheng-ming.md)
* [序](xu/xu.md)

### 立志篇

* [欢迎来到上海交通大学](li-zhi-pian/huan-ying-lai-dao-shang-hai-jiao-tong-da-xue.md)
* [失败的思维方式](li-zhi-pian/shi-bai-de-si-wei-fang-shi/)
  * [高考思维](li-zhi-pian/shi-bai-de-si-wei-fang-shi/gao-kao-si-wei.md)
  * [被动思维](li-zhi-pian/shi-bai-de-si-wei-fang-shi/bei-dong-si-wei.md)
* [反对PUA](li-zhi-pian/fan-dui-pua.md)
* [悲壮的学习方式](li-zhi-pian/bei-zhuang-de-xue-xi-fang-shi.md)
* [你的身价是多少](li-zhi-pian/ni-de-shen-jia-shi-duo-shao.md)
* [正确地浪费剩下的时间](li-zhi-pian/zheng-que-di-lang-fei-sheng-xia-de-shi-jian.md)
* [总有更值得做的事情](li-zhi-pian/zong-you-geng-zhi-de-zuo-de-shi-qing.md)
* [做研究的兴趣](li-zhi-pian/zuo-yan-jiu-de-xing-qu.md)
* [关于工作](li-zhi-pian/guan-yu-gong-zuo/)

### 访谈集

* [为了留学而出国](fang-tan-ji/untitled/)
  * [为什么要出国?](fang-tan-ji/untitled/wei-shen-me-yao-chu-guo.md)
  * [出国读什么学位什么专业?](fang-tan-ji/untitled/chu-guo-du-shen-me-xue-wei-shen-me-zhuan-ye.md)
  * [出国都有哪些步骤](fang-tan-ji/untitled/chu-guo-du-you-na-xie-bu-zhou.md)
  * [为了申请出国，大学期间需要准备什么](fang-tan-ji/untitled/wei-le-shen-qing-chu-guo-da-xue-qi-jian-xu-yao-zhun-bei-shen-me.md)
  * [警惕出国中介](fang-tan-ji/untitled/jing-ti-chu-guo-zhong-jie.md)
* [做真正的研究](fang-tan-ji/zuo-zhen-zheng-de-yan-jiu/)
  * [合理的研究态度](fang-tan-ji/zuo-zhen-zheng-de-yan-jiu/he-li-de-yan-jiu-tai-du.md)
  * [区分上学与研究](fang-tan-ji/zuo-zhen-zheng-de-yan-jiu/qu-fen-shang-xue-yu-yan-jiu.md)
  * [知识积累](fang-tan-ji/zuo-zhen-zheng-de-yan-jiu/zhi-shi-ji-lei.md)
  * [衡量学术价值](fang-tan-ji/zuo-zhen-zheng-de-yan-jiu/heng-liang-xue-shu-jia-zhi.md)
  * [一些常见误区](fang-tan-ji/zuo-zhen-zheng-de-yan-jiu/yi-xie-chang-jian-wu-qu.md)
* [管理者的智慧](fang-tan-ji/guan-li-zhe-de-zhi-hui/)
  * [御人先御己](fang-tan-ji/guan-li-zhe-de-zhi-hui/yu-ren-xian-yu-ji.md)
  * [培养团队](fang-tan-ji/guan-li-zhe-de-zhi-hui/pei-yang-tuan-dui.md)
  * [重在参与](fang-tan-ji/guan-li-zhe-de-zhi-hui/zhong-zai-can-yu.md)
  * [认识设计类课程](fang-tan-ji/guan-li-zhe-de-zhi-hui/ren-shi-she-ji-lei-ke-cheng.md)
  * [进度控制](fang-tan-ji/guan-li-zhe-de-zhi-hui/jin-du-kong-zhi.md)
* [保研者说](fang-tan-ji/bao-yan-zhe-shuo/)
  * [明确目的](fang-tan-ji/bao-yan-zhe-shuo/ming-que-mu-de.md)
  * [需要做些什么](fang-tan-ji/bao-yan-zhe-shuo/xu-yao-zuo-xie-shen-me.md)
  * [硕士之后](fang-tan-ji/bao-yan-zhe-shuo/shuo-shi-zhi-hou.md)
* [已经工作学长的人生经验](fu-lu/yi-jing-gong-zuo-xue-chang-de-ren-sheng-jing-yan/)
* [博士\(生\)学长们的经历](./)
* [小心项目的陷阱](fang-tan-ji/xiao-xin-xiang-mu-de-xian-jing/)
  * [辨别项目的质量](fang-tan-ji/xiao-xin-xiang-mu-de-xian-jing/bian-bie-xiang-mu-de-zhi-liang.md)
  * [选对导师](fang-tan-ji/xiao-xin-xiang-mu-de-xian-jing/xuan-dui-dao-shi.md)
  * [团队与合作伙伴](fang-tan-ji/xiao-xin-xiang-mu-de-xian-jing/tuan-dui-yu-he-zuo-huo-ban.md)
* [破解留沪政策](fang-tan-ji/po-jie-liu-hu-zheng-ce/)
  * [面对户口，我们应该持有什么样的心态](fang-tan-ji/po-jie-liu-hu-zheng-ce/mian-dui-hu-kou-wo-men-ying-gai-chi-you-shen-me-yang-de-xin-tai.md)
  * [户口审批制度是否规范？](fang-tan-ji/po-jie-liu-hu-zheng-ce/hu-kou-shen-pi-zhi-du-shi-fou-gui-fan.md)
  * [分！分！学生的命根！](fang-tan-ji/po-jie-liu-hu-zheng-ce/fen-fen-xue-sheng-de-ming-gen.md)
  * [其他琐碎问题](fang-tan-ji/po-jie-liu-hu-zheng-ce/qi-ta-suo-sui-wen-ti.md)

### 生存技巧

* [选课原则与选课技巧](sheng-cun-ji-qiao/untitled/)
  * [我是否一定要选二专？](sheng-cun-ji-qiao/untitled/wo-shi-fou-yi-ding-yao-xuan-er-zhuan.md)
  * [选课选什么](sheng-cun-ji-qiao/untitled/xuan-ke-xuan-shen-me.md)
  * [广占坑，占好坑](sheng-cun-ji-qiao/untitled/guang-zhan-keng-zhan-hao-keng.md)
* [人文、经管类课程](fu-lu/ren-wen-jing-guan-lei-ke-cheng/)
  * [必修类](fu-lu/ren-wen-jing-guan-lei-ke-cheng/bi-xiu-lei.md)
  * [选修类](fu-lu/ren-wen-jing-guan-lei-ke-cheng/xuan-xiu-lei.md)
* [突击备考](sheng-cun-ji-qiao/tu-ji-bei-kao/)
  * [注意复习范围](sheng-cun-ji-qiao/tu-ji-bei-kao/zhu-yi-fu-xi-fan-wei.md)
  * [三天冲刺](sheng-cun-ji-qiao/tu-ji-bei-kao/san-tian-chong-ci.md)
  * [考试结束后](sheng-cun-ji-qiao/tu-ji-bei-kao/kao-shi-jie-shu-hou.md)
  * [复习箴言](sheng-cun-ji-qiao/tu-ji-bei-kao/fu-xi-zhen-yan.md)
* [正确解读成绩算法](sheng-cun-ji-qiao/zheng-que-jie-du-cheng-ji-suan-fa/)
  * [GPA制度概览](sheng-cun-ji-qiao/zheng-que-jie-du-cheng-ji-suan-fa/gpa-zhi-du-gai-lan.md)
  * [伟大的选修课](sheng-cun-ji-qiao/zheng-que-jie-du-cheng-ji-suan-fa/wei-da-de-xuan-xiu-ke.md)
  * [理性挂科，合理重修](sheng-cun-ji-qiao/zheng-que-jie-du-cheng-ji-suan-fa/li-xing-gua-ke-he-li-zhong-xiu.md)
  * [风险与收益并存](sheng-cun-ji-qiao/zheng-que-jie-du-cheng-ji-suan-fa/feng-xian-yu-shou-yi-bing-cun.md)
* [旁门左道](sheng-cun-ji-qiao/pang-men-zuo-dao/)
  * [开学前两周的点名](sheng-cun-ji-qiao/pang-men-zuo-dao/kai-xue-qian-liang-zhou-de-dian-ming.md)
  * [理解“免听”](sheng-cun-ji-qiao/pang-men-zuo-dao/li-jie-mian-ting.md)
  * [形势政策考试](sheng-cun-ji-qiao/pang-men-zuo-dao/xing-shi-zheng-ce-kao-shi.md)
  * [物理实验](sheng-cun-ji-qiao/pang-men-zuo-dao/wu-li-shi-yan.md)
  * [学术灌水](sheng-cun-ji-qiao/pang-men-zuo-dao/xue-shu-guan-shui.md)

</details>


### Star History

<a href="https://www.star-history.com/#SurviveSJTU/SurviveSJTUManual&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=SurviveSJTU/SurviveSJTUManual&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=SurviveSJTU/SurviveSJTUManual&type=Date" />
   <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=SurviveSJTU/SurviveSJTUManual&type=Date" />
 </picture>
</a>

