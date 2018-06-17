

PATH = "teste.bmp"
IFB CHKIMG(PATH)
MSGBOX(PATH + "と同じイメージはX:" + G_IMG_X + ",Y:" + G_IMG_Y + "に表示されています。")
ELSE
MSGBOX(PATH + "と同じイメージはありませんでした。")
ENDIF



// 戻値 = CHKIMG( [画像名,　透過色/色無視,　x1,　y1,　x2,　y2,　番号,　色幅] )
// 引数
// 　画像名： 画像ファイル名（BMP形式のみ） （画像名を省略した場合はクリップボードから）
// 　透過色/色無視：
// 　　　　　 0： 指定なし （デフォルト）
// 　　　　　 1： 左上、2:右上、3:左下、4:右下　の１ピクセルの色を透過色として処理
// 　　　　　-1： 色を無視して形でチェックする
// 　x1,　y1,　x2,　y2： サーチ範囲
// 　番号： 複数ある場合に順番を指定 （左上から）
// 　　　　　-1：　-1が指定された場合はヒットした数を戻値として返し、座標情報は ALL_IMG_X[], ALL_IMG_Y[] に格納
// 　　　　　　　 （G_IMG_X、 G_IMG_Y には最後にヒットした位置が入る）
// 　色幅： チェックに色幅を持たせる　（色無視指定時もしくは 16bitカラー以下の場合は無効）
// 　　　　　IMG_MSK_BGR1　　// 各色(BGR)に対し 2/256の色幅を許す
// 　　　　　IMG_MSK_BGR2　　// 各色(BGR)に対し 4/256の色幅を許す
// 　　　　　IMG_MSK_BGR3　　// 各色(BGR)に対し 8/256の色幅を許す
// 　　　　　IMG_MSK_BGR4　　// 各色(BGR)に対し 16/256の色幅を許す
// 　　　　　IMG_MSK_B1, 2, 3, 4　　// 青に対し 2/256, 4/256, 8/256, 16/256の色幅を許す
// 　　　　　IMG_MSK_G1, 2, 3, 4　　// 緑に対し 2/256, 4/256, 8/256, 16/256の色幅を許す
// 　　　　　IMG_MSK_R1, 2, 3, 4　　// 赤に対し 2/256, 4/256, 8/256, 16/256の色幅を許す
// 　　　　　 ※ 演算可　例：IMG_MSK_B1 or IMG_MSK_R3（青に対し 2/256の色幅を許す + 赤に対し 8/256の色幅を許す）
// 戻値
// 　有ればTRUE、無ければFALSE
// 　TRUE の場合は見つかった座標を特殊変数　G_IMG_X、 G_IMG_Y に格納　　
// 　番号にて -1指定時はヒットした数を返し、座標情報は配列変数 ALL_IMG_X[], ALL_IMG_Y[] に格納（配列はゼロから）


//if chkimg(filename.bmp) then btn(LEFT,CLICK,G_IMG_X,G_IMG_Y)
//x = G_MOUSE_X
//y = G_MOUSE_Y
//btn(LEFT,DOWN)  上げる時はUPと書き込む

// FOR i = 1 TO 100
// IFB CHKIMG("bmp/ashipin" + i + ".bmp", 0, 1, 1, 500,500,1,IMG_MSK_BGR4)
// BTN(LEFT,CLICK,G_IMG_X, G_IMG_Y,10)
// ELSE
// ENDIF
// NEXT

// ↑の例だと認識対象のファイルが100ある場合、対象のファイル名をashipin1～ashipin100に変更して
// コードを実行するとashipin1から順番に100まで画像認識処理を繰り返す。

// dim imgfiles[3]
// imgfiles[1] = "敵1.bmp"
// imgfiles[2] = "敵2.bmp"
// imgfiles[3] = "敵3.bmp"
// for i=1 to 3
// ifb(CHKIMG(imgfiles[i])=TRUE) then
// BTN(LEFT, CLICK, G_IMG_X+2, G_IMG_Y + 2, 80)
// endif
// sleep(てきとうに)
// next


// // //
// // //
 
// // Dim RowNum   //ファイル内の行数を格納する変数をメモリ上に作成
// // Dim fid      //読み込むファイルのフィルのidを格納する変数をメモリ上に作成
// // Dim fid02    //書き出すファイルのフィルのidを格納する変数をメモリ上に作成
 
// // //読み込みたいファイルを開く（あらかじめ「D:\test01-2.txt」を作成しておきます。）
// // file = "D:\test01-2.txt"
// // fid = FOPEN(file,F_READ or F_WRITE)
 
// // //読み込みたいファイルの行数を取得
// // RowNum = FGET(fid,F_LINECOUNT) 
// // //MSGBOX("全部で" + RowNum + "行あります。")
 
 
// // Dim RowStr01[RowNum] //読み込んだファイルの全行の内容を格納するための配列の変数をメモリ上に作成
 
// // //配列「RowStr01」に、1行分ずつ、その内容を代入（TABなども含む）
// // for i = 1 to RowNum
// // 　RowStr01[i] = FGET(fid,i)　
  // // //MSGBOX(FGET(fid,i))
// // next
 
// // //読み込んだファイルを閉じる
// // FCLOSE(fid)
 
 
// // //＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
 
 
// // //書き込みたいファイルを開く
// // fid02 = FOPEN("D:\test02.txt", F_WRITE)
 
// // //※注：「F_WRITE」は、ファイルが存在しなければ自動生成し、
// // //       逆に存在すれば、ファイルの内容を上書きしてくれるそうです。
 
 
// // //読み込んだ全行の内容を配列変数の「RowStr01」から1行分ずつ書き込み
// // for i = 1 to RowNum
// // 　FPUT(fid02, RowStr01[i])
// // next
 
 
// // //書き込んだファイルを閉じる
// // FCLOSE(fid02)
 
// // MSGBOX("完了しました！")
 
// // //
// // //

// **********  出撃表示させるまで  **********
// // BTN(LEFT,CLICK,1254,39,203)  //艦これタブ押す
// // SLEEP(5.0)
// // ifb CHKIMG("KAN_HOW.bmp",0,200,120,1700,900)            // ☆画面補正開始
// // xx=G_IMG_X // 補正の為、画像の座標をxへ代入
// // yy=G_IMG_Y // 補正の為、画像の座標をyへ代入
// // xx=xx-703
// // yy=yy-725
 
// // else
// // Endif                                                   // ★画面補正終了
// // ifb CHKIMG("KAN_出撃.bmp",0,200,120,1700,900)          // ☆画面上に出撃が無かった場合以下
// // else
// // BTN(LEFT,CLICK,750,232,300)  // 母港１回押して表示させる
// // Endif                                                  // ★画面上に出撃が無かった場合終了
// // SLEEP(5.0)
// // ifb CHKIMG("KAN_出撃.bmp",0,200,120,1700,900)          // ☆画面上エラーだった場合以下
// // else
// // ifb CHKIMG("KAN_はい.bmp",0,200,120,1700,900)          // ☆☆画面上フラッシュエラーがあった場合以下
// // x=G_IMG_X // 画像の座標をxへ代入
// // y=G_IMG_Y // 画像の座標をyへ代入
// // BTN(LEFT, CLICK, x, y, 80)  // はいクリック
// // SLEEP(2.0)
// // Endif                                                  // ★★画面上フラッシュエラーがあった場合終了
// // BTN(LEFT,CLICK,837,69,300)  // DMM.COMログイン押す
// // SLEEP(5.0)
// // ifb CHKIMG("KAN_ﾛｸﾞｲﾝ.bmp",0,200,120,1700,900)         // ☆☆画面上ログインがあった場合以下
// // BTN(LEFT,CLICK,902,492,300)  // ログイン押す BTN  Left クリック x y 待ち時間
// // SLEEP(2.0)
// // Endif                                                  // ★★画面上ログインがあった場合終了
// // SLEEP(30.0)
// // for i=0 to 15
    // // ifb CHKIMG("KAN_出撃.bmp",0,200,120,1700,900)          // ☆☆画面上に出撃が無かった場合以下
    // // SLEEP(10.0)
    // // BTN(LEFT,CLICK,1308,579,300)  // GAME START押す
    // // else
    // // BREAK  // 出撃があったのでループ抜ける
    // // Endif                                                  // ★★画面上に出撃が無かった場合終了
// // NEXT  //i
// // Endif                                                  // ★画面上上エラーだった場合終了
// // SLEEP(2.0)
 
// // // **********  遠征中確認  **********
// // BTN(LEFT,CLICK,xx+900,yy+300,300)  // 編成押す 
// // SLEEP(3.0)
// // for j=875 to 937 STEP 31  // ２か３か４押す為のfor文
// // //    BTN(LEFT,CLICK,xx+900,yy+300,300)  // 編成押す
// // //    SLEEP(3.0)
    // // BTN(LEFT,CLICK,xx+j,yy+301,300)  // ２か３か４押す
    // // SLEEP(2.0)
    // // ifb CHKIMG("KAN_遠征中.bmp",0,200,120,1700,900)  // ☆遠征中だった場合以下
    // // CONTINUE  // 遠征中なので飛ばす
    // // else
    // // Endif                                            // ★遠征中だった場合終了
    // // SLEEP(3.0)
    // // if j<=906 then CONTINUE // ２か３なので飛ばす（906を875にすれば２だけ飛ばす）
    // // //ここから艦娘選択
    // // for yyy=403 to 629 STEP 113  // 縦列選択
        // // for xxx=1120 to 1462 STEP 342   // 横列選択
            // // MMV(xx+xxx,yy+yyy-82,300)  // マウス移動
            // // SLEEP(3.0)
            // // color=PEEKCOLOR(xx+xxx,yy+yyy-82)  // キラの位置色をcolorに記憶
            // // SLEEP(0.5)
            // // ifB PEEKCOLOR(xx+xxx,yy+yyy-82)<>color then            // ☆キラあるか確認
            // // SLEEP(0.5)
            // // ifB PEEKCOLOR(xx+xxx,yy+yyy-82)<>color then            // ☆☆キラあるか再度確認
            // // SLEEP(1.0)
            // // CONTINUE  //キラなので飛ばす
            // // else
            // // Endif                                            // ★★キラあるか再度確認終了
            // // else
            // // Endif                                            // ★キラあるか確認終了
 
            // // BTN(LEFT,CLICK,xx+xxx,yy+yyy,300)  // キラ無かったので変更押す
            // // SLEEP(1.0)
 
            // // for i=0 to 3  // キラ付け艦選択
                // // ifb CHKIMG("KAN_艦類確認.bmp",0,700,120,1700,750)  // ☆艦種類別があった場合以下
                // // BREAK  // 艦種類別があったのでループ抜ける
                // // else
                // // SLEEP(1.0)
                // // BTN(LEFT,CLICK,xx+1490,yy+293,300)  // ▽部分を押す
                // // MMV(xx+1450,yy+293,300)  // マウス移動
                // // SLEEP(1.0)
                // // Endif                                            // ★艦種類別があった場合終了
            // // next  // i
 
            // // BTN(LEFT,CLICK,xx+1424,yy+634,300)  // 最終のページ表示押す
            // // SLEEP(3.0)
            // // for x=1343 to 1103 STEP -30  // x枚目を選ぶためのfor～next
                // // if x<=1103 then break 3 // セット出来るキラ娘いないのでループ抜ける
                // // if x<=1253 then x=1253  // ５枚目以降を押すように細工
                // // BTN(LEFT,CLICK,xx+x,yy+634,300)  // x枚目のシートを押す
                // // SLEEP(2.0)
                // // ifb yyy=403 then  // ☆軽巡検出だった場合以下
                // // ifb CHKIMG("KAN_軽巡検索.bmp",0,700,120,1700,750)  // ☆☆軽巡がいなかった場合以下
                // // CONTINUE  //軽巡いないので飛ばす
                // // else
                // // Endif  // ★★軽巡がいなかった場合終了
                // // else
                // // Endif  // ★軽巡検出だった場合終了
 
                // // for y=350 to 602 STEP 28  // 上からy船目の艦種を選ぶためのfor～next
                    // // SLEEP(1.0)
                    // // ifb CHKIMG("KAN_２検出.bmp",0,700,yy+y-14,1700,yy+y+14)  // ☆２艦隊検出以下
                    // // CONTINUE  //艦隊所属しているので飛ばす
                    // // elseif CHKIMG("KAN_３検出.bmp",0,700,yy+y-14,1700,yy+y+14)  // ☆３艦隊検出以下
                    // // CONTINUE  //艦隊所属しているので飛ばす
                    // // elseif CHKIMG("KAN_４検出.bmp",0,700,yy+y-14,1700,yy+y+14)  // ☆４艦隊検出以下
                    // // CONTINUE  //艦隊所属しているので飛ばす
                    // // else
                    // // endif  // ★２．３．４艦隊検出終了
 
                    // // BTN(LEFT,CLICK,xx+1182,yy+y,300)  // 上からy船目の艦種押す
                    // // SLEEP(1.0)
                    // // ifb CHKIMG("KAN_ダメージ無し.bmp",0,700,120,1700,750)  // ☆ダメージ無しだった場合以下
                    // // else
                    // // BTN(LEFT,CLICK,xx+1182,yy+y,300)  // 艦種押す
                    // // CONTINUE  //ダメージあるので飛ばす
                    // // Endif  // ★ダメージ無しだった場合終了
 
                    // // ifb CHKIMG("KAN_キラ無.bmp",0,700,120,1700,750)  // ☆キラ無しだった場合以下
                    // // BTN(LEFT,CLICK,xx+1182,yy+y,300)  // 艦種押す
                    // // CONTINUE  //キラないので飛ばす
                    // // else
                    // // Endif  // ★キラ無しだった場合終了
 
                    // // ifb CHKIMG("KAN_変更.bmp",0,700,120,1700,750)  // ☆変更できる場合以下
                    // // else
                    // // BTN(LEFT,CLICK,xx+1182,yy+y,300)  // 艦種押す
                    // // CONTINUE  //変更無いしているので飛ばす
                    // // Endif  // ★変更できる場合終了
 
                    // // ifb yyy=403 then  // ☆軽巡検出だった場合以下
                    // // ifb CHKIMG("KAN_軽巡.bmp",0,700,120,1700,400)  // ☆☆軽巡だった場合以下
                    // // BTN(LEFT,CLICK,xx+1370,yy+622,300)  //変更押す
                    // // SLEEP(3.0)
                    // // break 2  //セットしたのでループ抜ける
                    // // else
                    // // BTN(LEFT,CLICK,xx+1182,yy+y,300)  // 艦種押す
                    // // CONTINUE  //軽巡じゃなかったので飛ばす
                    // // Endif  // ★★軽巡だった場合終了
                    // // else
                    // // ifb CHKIMG("KAN_駆逐.bmp",0,700,120,1700,400)  // ☆☆駆逐艦だった場合以下
                    // // BTN(LEFT,CLICK,xx+1370,yy+622,300)  //変更押す
                    // // SLEEP(3.0)
                    // // break 2  //セットしたのでループ抜ける
                    // // else
                    // // BTN(LEFT,CLICK,xx+1182,yy+y,300)  // 艦種押す
                    // // CONTINUE  //駆逐艦じゃないので飛ばす
                    // // Endif  // ★★駆逐艦だった場合終了
                    // // Endif  // ★軽巡検出だった場合終了
 
                // // next  //y
                // // SLEEP(1.0)
            // // next  //x
            // // SLEEP(1.0)
        // // next  //xxx
        // // SLEEP(1.0)
    // // next  //yyy
    // // SLEEP(1.0)
// // next  //j
 
// // // **********  補給  **********
// // BTN(LEFT,CLICK,xx+745,yy+398,300)  //補給押す
// // SLEEP(2.0)
// // for x=884 to 944 STEP 30
    // // BTN(LEFT,CLICK,xx+x,yy+301,300)  //２か３か４押す
    // // SLEEP(2.0)
    // // BTN(LEFT,CLICK,xx+825,yy+299,300)  //チェック押す
    // // SLEEP(2.0)
    // // BTN(LEFT,CLICK,xx+1403,yy+619,300)  //まとめて補給押す
    // // SLEEP(5.0)
// // next  //x
// // BTN(LEFT,CLICK,xx+750,yy+232,300)  //母港押す
// // SLEEP(5.0)
 
// // // **********  遠征  **********
// // for y=356 to 476 STEP 60
    // // if y=416 then y=566 // 警備任務を観艦式に変更
    // // ifb CHKIMG("KAN_出撃.bmp",0,200,120,1700,900)          //☆画面上に出撃が無かった場合以下
    // // else
    // // BTN(LEFT,CLICK,750,232,300)  //母港１回押して表示させる
    // // SLEEP(2.0)
    // // Endif                                                  //★画面上に出撃が無かった場合終了
    // // SLEEP(2.0)
    // // BTN(LEFT,CLICK,xx+902,yy+435,300)  //出撃押す
    // // SLEEP(2.0)
    // // BTN(LEFT,CLICK,xx+1380,yy+408,300)  //遠征押す
    // // SLEEP(2.0)
    // // ifb y=356 then // 練習航海をタンカー護衛任務に変更
    // // BTN(LEFT,CLICK,xx+910,yy+619,300)  //南西諸島海域押す
// // 　　else
// // 　  BTN(LEFT,CLICK,xx+850,yy+619,300)  //鎮守府海域押す
// // 　　Endif　
    // // SLEEP(2.0)
    // // BTN(LEFT,CLICK,xx+1114,yy+y,300)  //練習航海・警備任務・海上護衛任務押す
    // // SLEEP(2.0)
    // // ifb CHKIMG("KAN_決定.bmp",0,200,120,1700,900)           //☆決定あった場合以下
    // // BTN(LEFT,CLICK,xx+1380,yy+622,300)  //決定押す
    // // SLEEP(2.0)
    // // else
    // // CONTINUE  //決定がなかったのでforに戻る
    // // Endif                                                  //★決定あった場合以下終了
    // // SLEEP(2.0)
    // // for x=1100 to 1160 STEP 30
        // // BTN(LEFT,CLICK,xx+x,yy+303,300)  //２か３か４選んで押す
        // // SLEEP(2.0)
        // // ifb CHKIMG("KAN_!ﾏｰｸ.bmp",0,200,120,1700,900)          //☆画面上補給が終わってなかった場合以下
        // // else
        // // BTN(LEFT,CLICK,xx+1370,yy+622,300)  //遠征開始押す
        // // SLEEP(5.0)
        // // Endif                                                  //★画面上補給が終わってなかった場合終了
    // // next  //x
    // // SLEEP(2.0)
// // next  //y
// // BTN(LEFT,CLICK,xx+750,yy+232,300)  //母港押す
// // SLEEP(5.0)
 
// // // **********  入渠  **********
// // BTN(LEFT,CLICK,xx+835,yy+542,300)  //入渠押す
// // SLEEP(5.0)
// // ifb CHKIMG("KAN_ドック.bmp",0,700,120,1700,750)      //☆入渠できれば以下
// // x=G_IMG_X // 画像の座標をxへ代入
// // y=G_IMG_Y // 画像の座標をyへ代入
// // BTN(LEFT, CLICK, x, y, 300)     // empty押す
// // for i=320 to 410 STEP 30
// // SLEEP(1.0)
// // BTN(LEFT,CLICK,xx+1182,yy+i,300)  // 艦種押す
// // SLEEP(1.0)
// // ifb CHKIMG("KAN_入渠開始.bmp",0,700,120,1700,750)    //☆☆修理要なら以下
// // x=G_IMG_X // 画像の座標をxへ代入
// // y=G_IMG_Y // 画像の座標をyへ代入
// // BTN(LEFT, CLICK, x, y, 300)     // 入渠開始押す
// // SLEEP(5.0)
// // BTN(LEFT,CLICK,xx+1214,yy+581,300)  // はい押す
// // else
// // BTN(LEFT,CLICK,xx+1182,yy+i,300)  // 艦種押す
// // Endif   //★★修理要なら終了
// // next
// // else
// // Endif                                                //★入渠できれば終了
// // BTN(LEFT,CLICK,xx+750,yy+232,300)  //母港位置押す
 
// // // **********  キラ付け  **********
// // SLEEP(5.0)
// // BTN(LEFT,CLICK,xx+916,yy+320,300)  // 編成押す
// // SLEEP(5.0)
// // ifb CHKIMG("KAN_１検出.bmp",0,700,120,1700,750)  //☆１があった場合以下
// // SLEEP(1.0)
// // BTN(LEFT,CLICK,xx+1136,yy+301,300)  //随伴艦一括解除押す
// // SLEEP(1.0)
// // BTN(LEFT,CLICK,xx+850,yy+296,300)  // １の所を押す
// // SLEEP(1.0)
// // BTN(LEFT,CLICK,xx+1126,yy+398,300)  // 変更押す
// // SLEEP(1.0)
// // for i=0 to 3  // キラ付け艦選択
// // ifb CHKIMG("KAN_LV確認.bmp",0,700,120,1700,750)  //☆☆LVがあった場合以下
// // BREAK  //LVがあったのでループ抜ける
// // else
// // SLEEP(1.0)
// // BTN(LEFT,CLICK,xx+1490,yy+293,300)  // ▽LV部分を押す
// // MMV(xx+1450,yy+293,300)  //マウス移動
// // SLEEP(1.0)
// // Endif                                            //★★LVがあった場合終了
// // next
// // for x=1230+xx to 1470+xx STEP 30  // x枚目を選ぶためのfor～next
// // if x>=1320 then x=1320  //５枚目以降を押すように細工
// // BTN(LEFT,CLICK,x,627+yy,300)  // x枚目のシートを押す
// // SLEEP(1.0)
// // for y=350+yy to 602+yy STEP 28  // 上からy船目の艦種を選ぶためのfor～next
// // SLEEP(1.0)
// // BTN(LEFT,CLICK,xx+1182,y,300)  // 上からy船目の艦種押す
// // SLEEP(3.0)
// // ifb CHKIMG("KAN_ダメージ無し.bmp",0,1270,290,1700,380)  //☆☆ダメージ無しだった場合以下
// // ifb CHKIMG("KAN_キラ無.bmp",0,1270,290,1700,380)  //☆☆☆キラ無しだった場合以下
// // ifb CHKIMG("KAN_遠征中.bmp",0,1270,290,1700,380)  //☆☆☆☆遠征中でなかった場合以下
// // else
// // BTN(LEFT,CLICK,xx+1370,yy+622,300)  //変更押す
// // break 2  //セットしたのでループ抜ける
// // Endif                                             //★★★★遠征中でなかった場合終了
// // else
// // Endif                                             //★★★キラ無しだった場合終了
// // else
// // Endif                                             //★★ダメージ無しだった場合終了
// // BTN(LEFT,CLICK,xx+1182,y,300)  // 艦種押す
// // next
// // SLEEP(1.0)
// // next
// // SLEEP(7.0)
// // Endif  //★１があった場合終了
// // ifb CHKIMG("KAN_ダメージ無し.bmp",0,700,120,1700,750)  //☆旗艦がダメージ無しなら以下
// // SLEEP(3.0)
// // BTN(LEFT,CLICK,xx+740,yy+387,300)  //補給押す
// // SLEEP(2.0)
// // BTN(LEFT,CLICK,xx+863,yy+301,300)  //１押す
// // SLEEP(2.0)
// // BTN(LEFT,CLICK,xx+832,yy+299,300)  //チェック押す
// // SLEEP(2.0)
// // BTN(LEFT,CLICK,xx+1403,yy+619,300)  //まとめて補給押す
// // SLEEP(5.0)
// // BTN(LEFT,CLICK,xx+750,yy+232,300)  //母港押す
// // SLEEP(10.0)
// // BTN(LEFT,CLICK,xx+902,yy+435,300)  //出撃押す
// // SLEEP(5.0)
// // BTN(LEFT,CLICK,xx+950,yy+423,300)  //出撃押す
// // SLEEP(5.0)
// // BTN(LEFT,CLICK,xx+955,yy+423,300)  //鎮守府正面海域押す
// // SLEEP(5.0)
// // BTN(LEFT,CLICK,xx+1380,yy+622,300)  //決定押す
// // SLEEP(5.0)
// // ifb CHKIMG("KAN_!ﾏｰｸ.bmp",0,700,120,1700,750)          //☆☆画面上補給が終わってなかった場合以下
// // else
// // BTN(LEFT,CLICK,xx+1370,yy+622,300)  //出撃開始押す
// // for i=0 to 30  // 戦闘中
// // BTN(LEFT,CLICK,xx+974,yy+403,300)  //進撃  or  追撃せず押す
// // SLEEP(5.0)
// // BTN(LEFT,CLICK,xx+1350,yy+604,300)  //適当な位置クリック
// // SLEEP(5.0)
// // ifb CHKIMG("KAN_出撃.bmp",0,700,120,1700,750)          //☆☆☆画面上に出撃があった場合以下
// // break  // 戦闘終了確認できたので抜ける
// // else
// // Endif //★★★画面上に出撃があった場合終了
// // next
// // Endif //★★画面上補給が終わってなかった場合終了
// // SLEEP(2.0)
// // else
// // BTN(LEFT,CLICK,xx+750,yy+232,300)  //旗艦ダメージ有るので戦闘せず母港位置押す
// // SLEEP(5.0)
// // Endif //★旗艦がダメージ無しなら終了
 
// // // **********  解体  **********
// // SLEEP(5.0)
// // BTN(LEFT,CLICK,xx+980,yy+530,300)  // 工廠押す
// // SLEEP(2.0)
// // BTN(LEFT,CLICK,xx+950,yy+420,300)  // 解体押す
// // for i=0 to 3  // 解体艦選択
    // // ifb CHKIMG("KAN_LV確認.bmp",0,700,120,1700,750)  //☆☆LVがあった場合以下
    // // BREAK  //LVがあったのでループ抜ける
    // // else
    // // SLEEP(1.0)
    // // BTN(LEFT,CLICK,xx+1280,yy+293,300)  // ▽LV部分を押す
    // // MMV(xx+1450,yy+293,300)  //マウス移動
    // // SLEEP(1.0)
    // // Endif                                            //★★LVがあった場合終了
// // next  //i
// // SLEEP(3.0)
// // BTN(LEFT,CLICK,xx+1210,yy+634,300)  // 最終のページ表示押す
// // SLEEP(3.0)
 
// // for x=1129 to 1099 STEP -30  // x枚目を選ぶためのfor～next
    // // if x<=1039 then x=1039  // ５枚目以降を押すように細工
    // // BTN(LEFT,CLICK,xx+x,yy+634,300)  // x枚目のシートを押す
    // // SLEEP(2.0)
 
    // // for y=605 to 326 STEP -31  // 下からy船目の艦種を選ぶためのfor～next
        // // BTN(LEFT,CLICK,xx+1182,yy+y,300)  // 上からy船目の艦種押す
        // // SLEEP(1.0)
        // // ifb CHKIMG("KAN_解体駆逐艦１.bmp",0,700,120,1700,750)  // ☆解体する艦だった場合以下
        // // BTN(LEFT,CLICK,xx+1400,yy+620,300)  // 解体する押す
        // // SLEEP(7.0)
        // // elseif CHKIMG("KAN_解体駆逐艦２.bmp",0,700,120,1700,750)  // ☆解体する艦だった場合以下
        // // elseif CHKIMG("KAN_解体駆逐艦２.bmp",0,700,120,1700,750)  // ☆解体する艦だった場合以下
        // // BTN(LEFT,CLICK,xx+1400,yy+620,300)  // 解体する押す
        // // SLEEP(7.0)
        // // elseif CHKIMG("KAN_解体駆逐艦３.bmp",0,700,120,1700,750)  // ☆解体する艦だった場合以下
        // // BTN(LEFT,CLICK,xx+1400,yy+620,300)  // 解体する押す
        // // SLEEP(7.0)
        // // endif  // ★解体する艦だった場合検出終了
 
        // // BTN(LEFT,CLICK,xx+1182,yy+y,300)  // 上からy船目の艦種押す
        // // SLEEP(1.0)
    // // next  //y
    // // SLEEP(1.0)
// // next  //x
// // BTN(LEFT,CLICK,xx+750,yy+232,300)  //母港位置押す


// // // // // while true
	// // // // // ifb chkimg("go.bmp",0) //母港で出撃
		// // // // // x=G_IMG_X
		// // // // // y=G_IMG_Y
		// // // // // btn(left,click,x,y)
		// // // // // mmv(100,100.10)
		// // // // // sleep(5)
		
		
		// // // // // ifb chkimg("go2.bmp",0)
			// // // // // x=G_IMG_X
			// // // // // y=G_IMG_Y
			// // // // // btn(left,click,x,y)
			// // // // // sleep(4)
			
			// // // // // ifb chkimg("go1-1.bmp",0)
				// // // // // x=G_IMG_X
				// // // // // y=G_IMG_Y
				// // // // // btn(left,click,x,y)
				// // // // // sleep(2)
				
				// // // // // ifb chkimg("enter.bmp",0)
					// // // // // x=G_IMG_X
					// // // // // y=G_IMG_Y
					// // // // // btn(left,click,x,y)
					// // // // // sleep(1)
					// // // // // btn(left,click,x,y)
				// // // // // endif
			// // // // // endif
		// // // // // endif
	// // // // // endif
	
	// // // // // i=0
	// // // // // while i=0
		// // // // // ifb chkimg("hoq.bmp",0) //帰投したら補給
			// // // // // x=G_IMG_X
			// // // // // y=G_IMG_Y
			// // // // // i=1
			// // // // // btn(left,click,x,y)
			// // // // // sleep(3)
			
			// // // // // ifb chkimg("hoq2.bmp",0)
				// // // // // x=G_IMG_X
				// // // // // y=G_IMG_Y
				// // // // // btn(left,click,x,y)
				// // // // // btn(left,click,x+580,y+320)
			// // // // // endif
			// // // // // sleep(2)
			
			// // // // // ifb chkimg("home.bmp",0)
				// // // // // x=G_IMG_X
				// // // // // y=G_IMG_Y
				// // // // // btn(left,click,x,y)
				// // // // // mmv(100,100,1)
				// // // // // sleep(3)
			// // // // // endif
		// // // // // else
			// // // // // btn(left,click,x-370,y-180) //進撃位置の座標をクリック
			// // // // // sleep(1)
			// // // // // ifb chkimg("home.bmp",0)
				// // // // // x=G_IMG_X
				// // // // // y=G_IMG_Y
				// // // // // btn(left,click,x,y)
			// // // // // endif
		// // // // // endif
	// // // // // wend
// // // // // wend
