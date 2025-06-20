# 项目介绍
本项目基于公开数据库的宏基因组测序数据对比了强直性脊柱炎（AS）患者与健康人群的病毒组构成，对113例AS患者和37名健康受试者的肠道病毒群落进行了宏基因组学分析。通过对AS患者肠道病毒组的探索，更深入理解该疾病的病因学和发病机制，将有助于从新视角制定AS的防治策略。

# pipeline
1、参照final_proj.txt文件的1.1和1.2，进入shell命令界面，按照步骤完成数据下载，质量控制的预操作。

2、参照final_proj.txt文件的1.3，使用bowtie2软件进行比对去宿主，bowtie2软件下载请参照：https://github.com/BenLangmead/bowtie2

3、参照final_proj.txt文件的1.4，使用megahit对清理后的reads进行组装，megahit软件下载以及使用请参照：https://github.com/voutcn/megahit

4、参照final_proj.txt文件的1.5和1.6，使用checkv、deepvirfinder和VIBRANT对拼接后的contigs评估，筛选标准为：

  条件1: 移除真核生物基因数量 > 50% 的 contigs
  条件2: 移除真核生物基因数量 > 病毒基因数量的10倍的 contigs
  条件3: 至少有一个病毒基因，completeness≥50%
  DeepVirFinder 条件
  条件4: score > 0.90 且 p-value < 0.01
  VIBRANT 条件
  条件5: VIBRANT 识别的病毒

5、参照final_proj.txt文件的1.7和1.8，使用BUSCO评估初步筛选出的contigs是否大多数为病毒
  条件: 去除busco ratio > 5%

6、参照final_proj.txt文件的2，进行聚类和分类注释，最终得到物种注释表parent_lineage.tsv

7、参照final_proj.txt文件的3，计算vOTU的相对丰度并绘制物种丰度图

绘制帕累托图，代码文件pareto_getpro.txt

绘制科水平物种堆叠图，代码文件科丰度图.txt

绘制PCOA图，代码文件PCOA.txt

绘制α多样性图，计算香农、Simpson指数，代码文件α-diversity.txt

绘制科柱状图，选择有显著差异的科，代码文件科柱状图.txt ，显著科结果见科柱状图文件夹





