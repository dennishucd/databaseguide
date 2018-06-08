# Cypher Example 

## 杨绛

**创建节点**<br>
CREATE (yang:人物 {name:"杨绛", born_date:"1911年7月17日"}) return yang<br>
CREATE (qian:人物 {name:"钱钟书", born_date:"1910年10月20日"}) return qian<br>

**查询节点**<br>
MATCH (yang {name:"杨绛"}) return yang<br>
MATCH (yang) WHERE yang.name='杨绛' RETURN yang<br>
<br>
**创建关系**<br>
MATCH (yang {name:"杨绛"}), (qian {name:"钱钟书"})<br>
CREATE (yang)-[:Love {from:"1932"}]->(qian), (qian)-[:Love {from:"1932"}]->(yang)<br>
RETURN *<br>

**增加女儿关系**<br>
MATCH (yang {name:"杨绛"}), (qian {name:"钱钟书"})<br>
CREATE (yuan:人物 {name:"钱瑗"}), (yang)-[r1:母女]->(yuan), (qian)-[r2:父女]->(yuan)<br>
RETURN yang,qian,yuan,r1,r2<br>

**设置标签**<br>
MATCH (yang) WHERE yang.name='杨绛' SET yang:翻译家:文学家:戏剧家<br>
MATCH (qian) WHERE qian.name='钱钟书' SET qian:作家:文学研究家:翻译家<br>

**快速删除**<br>
MATCH (yang {name:"杨绛"}), (yang)-[r*0..2]->(n) detach delete n<br>

**快速创建**<br>
CREATE (yang:人物 {name:"杨绛", born_date:"1911年7月17日"}),<br>
       (qian:人物 {name:"钱钟书", born_date:"1910年10月20日"}),<br>
       (yuan:人物 {name:"钱瑗"}),<br>
       (yang)-[:爱 {from:"1932"}]->(qian),<br>
       (yang)-[:爱 {from:"1932"}]->(qian),<br>
       (yang)-[r1:母女]->(yuan),<br>
       (qian)-[r2:父女]->(yuan)<br>
RETURN *<br>

MATCH (yang) WHERE yang.name='杨绛' SET yang:翻译家:文学家:戏剧家<br>
MATCH (qian) WHERE qian.name='钱钟书' SET qian:作家:文学研究家:翻译家<br>
<br>

##  林徽因
**图谱建立**<br>
CREATE (lin:人物 {name:"林徽因", born_date:"1904年6月10日"}),<br>
              (liang:人物 {name:"梁思成", born_date:"1901年4月20日"}),<br>
              (xu:人物 {name:"徐志摩"}),<br>
              (jin:人物 {name:"金岳霖"}),<br>
              (zhang:人物 {name:"张幼仪"}),<br>
              (lu:人物 {name:"陆小曼"}),<br>
              (qichao:人物 {name:"梁启超"}),<br>
              (zaibing:人物 {name:"梁再冰"}),<br>
              (lin)-[:丈夫]->(liang),<br>
              (lin)-[:情人]->(xu),<br>
              (lin)-[:女儿]->(zaibing),<br>
              (liang)-[:父亲]->(qichao),<br>
              (lin)-[:情人]->(jin),<br>
              (xu)-[:前妻]->(zhang),<br>
              (xu)-[:妻子]->(lu)<br>
RETURN *<br>
       
**查询**<br>
[1] 跟林徽因有直接关系的人物<br>
MATCH (lin {name:"林徽因"}), (lin)-[r*1]->(n) return n<br>
MATCH (lin {name:"林徽因"}), (lin)-[r]->(n) return n<br>
<br>
[2] 跟林徽因间接关系的人物<br>
MATCH (lin {name:"林徽因"}), (lin)-[r*2]->(n) return n<br>
