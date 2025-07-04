## 启动

在 Ubuntu20.04 ROS noetic 版本测试成功

`roslaunch rviz_map_editor rviz_edit.launch`

line 工具用于绘制一条直线，单击后，它会像测量函数一样拉伸，如果再次单击所需的位置，则直线完成。此时，可以连续绘制，而无需单击顶部栏来绘制下一条直线。

remove 工具是使用快捷键“r”擦除创建的，单击时，会创建一个直径为 2m 的圆，您可以将其放在要擦除的位置。

## 设置

将需要修改的地图文件`map.pgm` 和 `map.yaml` 存放到 `rviz_map_editor/original_map` 文件夹中,并修改 `rviz_edit.launch` 中的对应的参数

## 注意

1. 行为无法撤销,如果操作失误只能重新启动

2. 修改完成后,关闭节点 pgm 文件自动保存到 `rviz_map_editor/edited_map` 路径下,文件名在 `rviz_edit.launch` 中修改

3. 如果想对一个文件进行多次修改,请在编辑前修改保存的文件名,不然会覆盖之前编辑的文件

---

原仓库地址: https://github.com/sunghowoo/rviz_map_editor

以下是原作者 readme

## Manual

작성자 : 우성호 , 작성일지: 2021/11/25

#### 목적 : rviz 를 이용해서 스캔 값을 기준으로 간단히 맵 (.pgm)를 수정한다

Youtube: https://www.youtube.com/watch?v=WKNOM6503FI&ab_channel=SunghoWoo

---

Installation : Rviz_map_editor Repo를 사용자 컴퓨터에 make를 하면 자동으로 Rviz tool 까지 깔린다. (편안..)

---

#### 사용전세팅:

1. 바꾸고자하는 map.pgm 을 로봇에서 가져와 rviz_map_editor/original_map안에 넣는다.

2. launch 폴더안에 rviz_edit.launch를 실행하기전 로봇RID 세팅 및 파일 로드 ,세이브 경로를 세팅한다.

---

#### Rviz 세팅 및 Tool 기능

1. 상단창에 + 모양을 클릭하고 rviz_map_editor 폴더안에 Line tool 과 Remove tool을 클릭해 위치 시킨다

   <details>
       <summary> 사진 첨부</summary>
       <img src="media/1.png" alt="1" style="zoom:50%;" /> -->
   </details>

2. remove tool은 지우는용도로써 단축기 ' r ' 을 이용하면 생성되고 클릭되면 지름 2m 인 원모양이 생성되어 지우고 싶은곳에 내려놓으면된다.

3. line tool은 직선을 그리는 용도로 한번 클릭되면 measure기능처럼 쭉 늘어나 원하는 곳을 다시 클릭하면 직선이 완성된다. 이때 다음 직선을 그리기위해 상단 바를 클릭할 필요없이 연속 그리기가 가능하다.

   <details>
       <summary>영상 첨부</summary>
       <img src="media/2.gif" style="zoom:67%;" />
   </details>

---

#### 사용과정

1. rviz_edit.launch를 실행하면 시작한다는 문구가 뜨며 그떄부터 Rviz 로부터 토픽을 받아온다.

2. \*\* rviz에서 부터 클릭된 순간 취소할 수없어 신중하게 클릭해야한다. 다시 하기위해선 rviz를 재시작 , rviz_edit 재시작이 필요하다

3. 모든곳을 수정했으면 rviz_map_editor노드를 종료(ctrl + c) 를 하게 되고 자동저장이 된다.

4. ** 실제로 로봇에 넣기전 수정한 맵을 nano를 열어 한줄을 추가해줘야한다. original map에서 nano로 켜보면 '' **# CREATOR: map_saver.cpp 0.050 m/pix ''\*\* 이란 문구가있는데 이를 수정된 파일에도 동일하게 삽입하여 저장해준다 . ( map server를 거치지않는 pgm 파일을 수정하므로 # 이 붙지않는다. Software 2팀이 맵을 읽어올때 (#) 필요하단 사실..!)

   <details>
       <summary>영상 첨부</summary>
       <img src="media/3.png" style="zoom: 80%;" />
   </details>
