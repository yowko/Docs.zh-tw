---
title: F# Interactive 選項
description: 深入了解所支援的命令列選項F#Interactive fsi.exe。
ms.date: 05/16/2016
ms.openlocfilehash: cca1ef6671878acb1b837d6590139d5de7b7167d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996797"
---
# <a name="f-interactive-options"></a>F# Interactive 選項

> [!NOTE]
> 本文目前僅描述 Windows 的體驗。  將會加以重新撰寫。

本主題說明所支援的命令列選項F#Interactive， `fsi.exe`。 F#Interactive 接受許多與相同的命令列選項F#編譯器，但也接受某些其他選項。

## <a name="using-f-interactive-for-scripting"></a>使用F#互動式指令碼處理
F#互動式、 `fsi.exe`、 可以互動方式啟動或從命令列執行指令碼就可以啟動。 命令列語法

```
> fsi.exe [options] [ script-file [arguments] ]
```

該檔案的副檔名F#指令碼檔案是`.fsx`。

## <a name="table-of-f-interactive-options"></a>資料表的F#Interactive 選項
下表摘要說明所支援的選項F#互動。 在命令列上或透過 Visual Studio IDE，您可以設定這些選項。 若要在 Visual Studio IDE 中設定這些選項，開啟**工具**功能表上，選取**選項...**，然後展開**F#工具**節點，然後選取**F#互動式**。

清單中出現的位置F#互動式選項引數，清單項目會以分號 (`;`)。

|選項|描述|
|------|-----------|
|**--**|用來指示F#Interactive 將剩下的引數視為命令列引數F#程式或指令碼，您可以在程式碼中使用清單**fsi.CommandLineArgs**。|
|**--checked**[**+**&#124;**-**]|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--codepage:&lt;int&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--consolecolors**[**+**&#124;**-**]|輸出警告和錯誤訊息中的色彩。|
|**--crossoptimize**[**+**&#124;**-**]|啟用或停用跨模組最佳化。|
|**--debug**[**+**&#124;**-**]<br /><br />**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--define:&lt;string&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--deterministic**[**+**&#124;**-**]|產生的具決定性的組件 （包括模組版本 GUID 與時間戳記）。|
|**--exec**|指示F#interactive 在載入檔案或執行命令列上指定的指令檔之後結束。|
|**--fullpaths**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--gui**[**+**&#124;**-**]|啟用或停用 Windows Forms 事件迴圈。 會啟用預設值。|
|**--help**<br /><br />**-?**|用來顯示命令列語法和每個選項的簡短描述。|
|**--lib:&lt;folder-list&gt;**<br /><br />**-I:&lt;資料夾清單&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**-載入：&lt;檔名&gt;**|編譯指定的原始碼在啟動並載入已編譯F#建構的工作階段。 如果包含指令碼指示詞，例如目標來源 **#use**或 **#load**，則您必須使用 **-使用**或是 **#use**而不是 **-載入**或是 **#load**。|
|**--mlcompatibility**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--noframework**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)|
|**--nologo**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--nowarn:&lt;warning-list&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--optimize**[**+**&#124;**-**]|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--preferreduilang:&lt;lang&gt;**| 指定慣用的輸出語言的文化特性名稱 （例如 ES-ES、 JA-JP）。 |
|**--quiet**|隱藏F#的輸出傳送至互動式**stdout**資料流。|
|**--quotations-debug**|指定的額外的偵錯資訊應該發出衍生自運算式的F#引號常值及反映的定義。 偵錯資訊加入自訂屬性的F#運算式樹狀節點。 請參閱[程式碼引號](code-quotations.md)並[Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3)。|
|**--readline**[**+**&#124;**-**]|啟用或停用在互動模式中的 tab 鍵自動完成。|
|**-參考：&lt;檔名&gt;**<br /><br />**-:&lt;檔名&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--shadowcopyreferences**[**+**&#124;**-**]|防止遭到鎖定藉由參考F#互動式處理序。|
|**--simpleresolution**|解決使用目錄為基礎的規則，而不是 MSBuild 解析的組件參考。|
|**--tailcalls**[**+**&#124;**-**]|啟用或停用的結尾的 IL 指令，這會導致尾端遞迴函式重複使用的堆疊框架。 這個選項預設為啟用。|
|**--targetprofile:&lt;string&gt;**|指定這個組件的目標 framework 設定檔。 有效值為 mscorlib、 netcore 或 netstandard。  預設為 mscorlib。|
|**-使用：&lt;檔名&gt;**|告訴解譯器將啟動指定的檔案做為初始輸入。|
|**--utf8output**|和 fsc.exe 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--warn:&lt;warning-level&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--warnaserror**[**+**&#124;**-**]|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----|-----------|
|[編譯器選項](compiler-options.md)|描述可用的命令列選項F#編譯器**fsc.exe**。|
