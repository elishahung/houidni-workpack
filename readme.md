Eli's Houdini Workpack
===
:::info
- 這是夢想動畫的houdini工具套件
- ==標題被標示黃底的==，代表尚在開發的套件，可能會遇到問題
- 安裝方法 (二選一)：
A - 將 `Q:\resource\houdini.env` 複製到 `C:\Users\使用者名稱\Documents\houdini16.5` 並覆蓋
B - 直接打開 `C:\Users\使用者名稱\Documents\houdini16.0\houdini.env`
並在最後加上兩行
`HOUDINI_OTLSCAN_PATH="Q:/resource/houdini;@/otls"` `HOUDINI_MENU_PATH="Q:/resource/houdini;@/"`
- 使用方式：
指令在選單列`MoonShine`底下，節點在`TAB Menu`的`Elisha's Tools`底下
:::

指令
===
![](https://i.imgur.com/QeFB6w2.png)
- Link Bound / 連結模擬限制框
快速將模擬的外框size跟pivot連結到指定的物件
- Link Parm / 連結參數
快速連結節點大小或中心給參數
- Add Vex Function / 增添公式
對一些常用的公式做懶人包
  - 兩向量夾角 : 兩個向量的角度
  - 動畫控制 : 繭繭私密配方，詳情來找我yo
- Create Rop From Cache / 將cache包成rop給deadline放模擬
- Help / 套件說明
開啟套件說明網頁

節點
===

## Animated Bound / 動態外框
![](https://i.imgur.com/bPYWp88.png)
>__動態範圍的bounding box__

指定時間範圍取出最大的bounding範圍
- Frame : 時間範圍
- Calculate : 按下開始計算
- Lower Padding : 同bound參數
- Upper Padding : 同bound參數

## Attribute to Material / 依屬性創建材質
![](https://i.imgur.com/SOcuWyr.png)
>__根據屬性創建相對應材質__

主要是給FBX輸出用，常搭配[Group to Attribute](#group-to-attribute--%E7%BE%A4%E7%B5%84%E8%BD%89%E6%8F%9B%E6%88%90%E5%B1%AC%E6%80%A7)做使用
- Attribute Name : 對應的屬性，右邊箭頭下拉有目前屬性方便選取
- Delete Attribute : 對應後刪除屬性
- Refresh : 強制更新材質

## Batch Schedule / 佇列排程執行 
![](https://i.imgur.com/D0bpmDm.png)
>__將模擬或算圖排程執行並在完成時獲得通知與經過時間__
- Node : 將要排程的節點拖曳到此欄位
- Add to List : 按此按鈕加入排程佇列
- Relative : 用相對路徑的方式加入節點，以維持架構
- Batch List : 排程佇列，前面勾勾可以略過排程，也可在此手動添加/更改節點
- Email : 可以勾選在排程完成後寄信通知，如果寄信成功，此欄位的電子信箱會自動儲存在電腦裡

## Camera Cone / 攝影機視角範圍生成
![](https://i.imgur.com/LKy0yIj.png)
>__依照攝影機視角產生六面體模型__
- Camera : 選擇攝影機
- Near : 攝影機起始的Z值
- Far : 攝影機終點的Z值
- X Offset : 攝影機寬度的微調
- Y Offset : 攝影機高度的微調

## Compute Velocity / 速度計算
![](https://i.imgur.com/UWxpuVR.png)
>__取代trail的快速運算__
- Match Attribute : 屬性配對，通常是id或name

## Crop by Camera / 攝影機裁切
![](https://i.imgur.com/pcoYPqV.png)
>__依照攝影機視野去做裁切__
- Camera : 指定要裁切的攝影機
- Frame Offset : X與Y軸框架的微調
- Crop Z / Z Offset : Z軸的裁切

## Duplicate Wires / 線條複製
![](https://i.imgur.com/k53tp2p.png)
>__將線條以自身為中心，複製多份__
- Radius : 複製線條的半徑
- Amount : 線條數量

## Edge Group to Curve / 邊線群組轉換線條
![](https://i.imgur.com/YmBl0nD.png)
>__將物件的Edge群組取出成線條__
- Group : Edge群組選擇，右邊箭頭可下拉快速選取
- Fuse Vertices : 連結所有線條

## Export Pack to FBX / Pack物件輸出FBX
![](https://i.imgur.com/6kRO708.png)
>__將Pack物件動態分成個體輸出FBX__

主要是用在碎裂特效輸出到3ds Max或遊戲軟體，在面數與物件不多的情況之下，對空間與效能節省許多，可調性也比較高。

- Output File : 輸出FBX的路徑
- Start/End : 開始與結束影格
- Scene Scale : 場景大小

## Export Point Cache / 輸出Point Cache
![](https://i.imgur.com/pVQGHyw.png)
>__輸出給MAX和MAYA讀取的FBX與PC2檔，注意要三角面__
- Export : 輸出FBX和PC2
- Export Cache Only : 只輸出PC2
- Start/End : 輸出影格範圍
- Export Path : 輸出路徑
- File Name : 檔案名稱

## Export to AE / 將物件跟攝影機輸出到AE
![](https://i.imgur.com/ouBG1Nq.png)
>__產生可讓AE讀取物件位置跟攝影機動態的檔案__

物件部分目前只可讀最外層的obj，之後會想改良成point位置會比較方便

## Extract Matrix / 分析位移資訊
![](https://i.imgur.com/vV7dghn.png)
>__將只有頂點動態的物件分析出Matrix資訊__
- Cache Trasnsform Data : 將分析資訊儲存cache
- Geometry File : cache儲存位置
- Group Similar Transform : 將類似的位移物件群組起來
- Visualize Groups : 顯示不同群組
- Grp Threshold : 群組位移資訊的相似度
- Frame : 群組判斷的格數

## Grid Points / 產生格點
![](https://i.imgur.com/GbUElEQ.png)
>__對物體產生等距格點__
- Length : 點與點之間的距離
- Expand : 範圍的延伸或縮減

## Group to Attribute / 群組轉換成屬性
![](https://i.imgur.com/SEAs3ba.png)
>__將群組變成字串屬性，群組名稱為屬性值__
- Attribute Name : 轉換成的屬性名稱，右邊下拉箭頭有預設項目
- Delete Groups : 轉換後刪除群組

## Keep Biggest Part / 保留最大區塊
![](https://i.imgur.com/hZ5Rppz.png)
>__利用connectivity區分部件，並只保留最大體積區塊__

## Material from 3dsMax / 繼承3dsMax材質
![](https://i.imgur.com/6INO0OT.png)
>__取得max場景物件的材質資訊，並重新上回在houdini的alembic，以及最後到max的VrayProxy材質重新對應回去__
- Get Max Script : 開啟含有maxscript的資料夾，裏頭有兩個script
    -- `A_getMaterial` : 在3dsMax裡選取要取得材質資訊的物件並執行，會將資訊複製到剪貼簿，然後再貼到Material Data的欄位上
    -- `B_applyMaterial` : 在3dsMax匯入VrayProxy後，選取並執行，將材質對應回去
- Material Data : 將`A_getMaterial`執行產生的資訊貼在此處
- Attribute Name : 材質資料的屬性名稱

## Merge to Class / 合併並分類
![](https://i.imgur.com/km73Qjv.png)
>__將輸入的節點merge並依輸入順序設定class屬性__

## Patch Particles / 粒子填充
![](https://i.imgur.com/ce53PJt.png)
>__將每格粒子數量補足成最後的數量，主要用在破碎碎粒可以做成頂點動畫__
- Input0 : 粒子動畫
- Input1 : 最後一格的粒子

## Quick Bound Clip / 快速方塊切割
![](https://i.imgur.com/2LZ3L2N.png)
>__給予一個方塊(可旋轉)，將模型快速裁切在BOX裡面__

## Rotate Prims / 剝皮
![](https://i.imgur.com/BYQB1yA.png)
>__將Primitive針對參考點去捲動，類似剝皮的效果__
- Time : 動畫時間點
- Range : 每個轉換過程佔據整體時間的比例
- Flip Direction : 相反旋轉方向
- Amount : 旋轉的強度
- (Rotation) Progress Curve : 旋轉動畫的過程曲線
- (Shrink) Progress Curve : 縮小動畫的過程曲線
- Remove Empty Primitives : 移除縮到看不見的面
- Remove Computed Attributes : 移除中途計算的屬性

## Seperate / 物件分類
![](https://i.imgur.com/EyMS93W.png)
>__用選取方式將物件拆解分成不同部位__
- Create Node to Parts : 根據群組產生各自節點
- Visualize : 用顏色標示每個群組
- Hide Other Parts When Select : 選取群組時，將現有群組隱藏，以避免誤選
- Attribute : 分類的屬性名稱
- Group Name : 該部位的群組名稱，空白的話不會建立群組
- Primitives : 選取的面編號，按右邊箭頭來選取
- Solo : 單獨顯示部位

## Seperate EXR channels / EXR拆通道 (COP)
![](https://i.imgur.com/xemiPmz.png)
>__將多通道的EXR照公司算圖方式拆開到各別資料夾__
- File : 要拆的EXR序列
- Reload : 重新讀取一次
- Start / End : 開始與結束的影格
- Output Elements : 預覽會拆開的元件跟檔名
- Render (Controls) : 算圖跟細項(依影格順序算或元件順序算)

## Tension / 張力分析
![image alt](https://i.imgur.com/2M7y0Pl.png)
>__網路的套件，藉由參照物件找出扭曲改變的部分__

## Transform by Alembic / 跟隨Alembic位移
![image alt](https://i.imgur.com/AGTI4nL.png)
>__找出Alembic的位移資訊並套用__

## Transform by Axis / 根據軸向位移
![](https://i.imgur.com/Aw0FmEB.png)
>__找出最相符的軸向並依此型變__
- Axis order : 依照三軸長度由升序排列
- Translate : 位移
- Rotate : 旋轉
- Scale : 縮放

## ==Transform by Matrix / 相對Matrix位移==
![image alt](https://i.imgur.com/A0rWEMZ.png)
>__前一個節點的進階版，抓出input1跟input2的matrix相對位移資訊來移動__
- Input0 : 要位移的物件
- Input1 : 參考物件
- Input2 : 動態物件

## VDB Merge / 合併VDB
![](https://i.imgur.com/YhQBBoh.png)
>__合併同一節點的所有VDB__

## Volume Vector Visualize / 顯示體積資訊
![image alt](https://i.imgur.com/VQyZ1ua.png)
>__視覺化體積資訊，主要用在Vel__
- Attribute : 要顯示的體積屬性
- Plane : 資訊的切面方向
- Offset : 切面的位移
- Trail Length : 顯示的拖尾長度

## VR Flipbook / VR預覽
![image alt](https://i.imgur.com/O9Zl60m.png)
>__產生360預覽__
- Start/End : 擷取範圍
- Output Path : 輸出路徑
- Filename : 檔案名稱
- Camera : 要產生的相機
- Resolution : 解析度
- Export Video : 將預覽轉檔成影片，並選擇是否保存原始圖檔序列
- CubeToSphere Path : 應用程式的路徑
- FFMpeg Path : 應用程式的路徑

流程工具
===
## Moonshine Cache Export / Cache交接輸出
![](https://i.imgur.com/uMcLtxC.png)
>__對MAYA流程的Cache輸出，交接備註與管理__
- Cache資料夾路徑 : 當設定好專案資訊後會顯示路徑，可複製
- 硬碟代號 : 選擇要存在Q槽或者D槽
- Export按鈕 : 輸出Cache，如果是第一次建立該Cache也會新增必須的資料夾
- 資料夾按鈕 : 打開保存Cache的資料夾
- 複製按鈕 : 從另一個硬碟代號將Cache複製過來，譬如現在在Q槽的某cache_v2，就會從D槽的某cache_v2把檔案複製過來，方便在本機模擬完後再轉移到網路伺服器
- User : 輸出Cache的使用者名稱
- Project : 專案名稱
- Cut : 卡號
- Name : Cache名稱
    -- Name右邊按鈕 : 如果有設定好專案跟卡號，可以直接按此按鈕讀取該卡號的Cache資訊
- Version : 版本號
    -- Add Comment : 增加該版本號備註
- 交接留言板
    -- 重新整理按鈕 : 重新整理Cache交接留言板
    -- 中間文字 : 最新一則交接留言版的留言
    -- 氣泡框按鈕 : 觀看所有留言跟新增留言
- Valid Frame Range : 影格輸出方式
- Start/End/Inc : 影格輸出範圍
- Scene Scale : 場景大小
- Seprate : 分別設定場景大小的三軸
- Type : 選擇要輸出Alembic還是VDB
- Alembic : 
    -- Render Full Range : 勾選時輸出為一個alembic，取消勾選則輸出多個alembic
    -- Build Hierarchy From Attribute : 由自訂屬性創立階層關係
    -- Path Attribute : 自訂階層屬性
- VDB :
    -- Write 16-Bit Floats : 寫入16位元浮點數格式，壓縮節省Cache空間