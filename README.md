## 目录说明

* JavaDoc：项目JavaDoc文档。
* TW-HomeWork：项目所处位置。

## JavaDoc说明：

* 打开JavaDoc/index.html,可查看Main类和TestMain类中方法的说明。
* TestMain中所列出的方法即各种不同的测试用例输入，可直接运行TestMain类查看运行结果

## 项目设计思路

PS:设计思路描述时所用数据格式解析说明:  

* e4e87cb2-8e9a-4749-abb6-26c59344dfee//第一个Id所对应的快照(即第一条记录)  
2016/09/02 22:30:46  
cat1 10 9

* 351055db-33e6-4f9b-bfe1-16f1ac446ac1//第二个Id所对应的快照(即第二条记录)  
2016/09/02 22:30:52//时间  
cat1 10 9 2 -1//第一个动物快照  
cat2 2 3//第二个动物快照

* dcfa0c7a-5855-4ed2-bc8c-4accae8bd155//第三个Id所对应的快照(即第三条记录)  
2016/09/02 22:31:02  
cat1 12 8 3 4

1. 将输入historyData按全局Id存入数组recodsArray，数组每个元素为一个Id所对应的快照

2. 对recodsArray进行遍历,逐个获取每条记录的所有动物快照存入map
   * 如果遍历已达到所查找的 Id，则停止并返回map中所存储的所有快照。
   * 如果获取单条记录的动物快照时返回false，则输出errMsg(如果格式错误等问题是发生在所查找Id之后，则不报错，正常输出结果；如果此种情况依然需要报错，则一直遍历到数组结束)

3. 获取单条记录的动物快照时，先验证该条记录格式的正确性，（行数、id格式、时间格式等）
   * 若格式错误，则设置errMsg并返回false，结束遍历；
   * 若格式正确，则取出该记录中动物的位置信息加入map(遍历取出所有)
     加入map时：验证动物位置信息格式（放在此处验证而没有在上面一块验证，是为了减少遍历次数）
        * 若动物位置信息格式正确：  
	     * 若map中已有该动物，比较与已有动物快照是否相对应，是则更新，否则设置errMsg，并返回false。  
	     * 若map中没有该动物，则直接加入。
	* 若动物位置信息格式错误:  
	     * 设置errMsg并返回false，结束遍历；

4. 当步骤2遍历结束时，map中即为Id时刻的所有动物快照。

## 设计流程图

![image]()



