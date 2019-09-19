---
title: F# Interactive 選項
description: 瞭解F#互動式 fsi.exe 所支援的命令列選項。
ms.date: 05/16/2016
ms.openlocfilehash: c9cd5c2e73a6e2f6ce0a9b2f2a631b6a2658423c
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083124"
---
# <a name="f-interactive-options"></a>F# Interactive 選項

> [!NOTE]
> 本文目前僅描述 Windows 的體驗。  將會加以重新撰寫。

本主題描述F#互動式`fsi.exe`所支援的命令列選項。 F#互動式接受許多與F#編譯器相同的命令列選項，但也接受一些額外的選項。

## <a name="using-f-interactive-for-scripting"></a>使用F# Interactive 進行腳本處理
F#互動式， `fsi.exe`可以互動方式啟動，也可以從命令列啟動以執行腳本。 命令列語法為

```console
> fsi.exe [options] [ script-file [arguments] ]
```

F#腳本檔案的副檔名為`.fsx`。

## <a name="table-of-f-interactive-options"></a>互動式選項F#的資料表
下表摘要說明F#互動式支援的選項。 您可以在命令列上或透過 Visual Studio IDE 來設定這些選項。 若要在 Visual Studio IDE 中設定這些選項，請開啟 [**工具**] 功能表，選取 [**選項 ...** ]，然後展開 [  **F#工具**] 節點並選取 **F# [互動式**]。

清單元素會以F#分號（`;`）分隔，其中清單會出現在互動式選項引數中。

|選項|描述|
|------|-----------|
|**--**|用來指示F#互動式將其餘引數視為程式或腳本的F#命令列引數，您可以使用清單**fsi.exe. my.application.commandlineargs**，在程式碼中存取。|
|**--checked**[ **+** &#124; **-** ]|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--codepage:&lt;int&gt;**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--consolecolors**[ **+** &#124; **-** ]|以色彩輸出警告和錯誤訊息。|
|**--crossoptimize**[ **+** &#124; **-** ]|啟用或停用跨模組優化。|
|**--debug**[ **+** &#124; **-** ]<br /><br />**--debug:** [**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]<br /><br />**-g**[ **+** &#124; **-** ]<br /><br />**-g:** [**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--define:&lt;string&gt;**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--deterministic**[ **+** &#124; **-** ]|產生具決定性的元件（包括模組版本 GUID 和時間戳記）。|
|**--exec**|指示F#在載入檔案或執行命令列上指定的腳本檔案之後，以互動的狀態結束。|
|**--fullpaths**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--gui**[ **+** &#124; **-** ]|啟用或停用 Windows Forms 事件迴圈。 會啟用預設值。|
|**--help**<br /><br />**-?**|用來顯示命令列語法，以及每個選項的簡短描述。|
|**--lib：&lt;資料夾-清單&gt;**<br /><br />**-I：&lt;資料夾清單&gt;**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--load：&lt;filename&gt;**|在啟動時編譯指定的原始程式碼，並將編譯F#的結構載入會話。 如果目標來源包含腳本指示詞，例如 **#use**或 **#load**，則您必須使用 **--use**或 **#use** ，而不是 **--load**或 **#load**。|
|**--mlcompatibility**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--noframework**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)|
|**--nologo**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--nowarn：&lt;warning-list&gt;**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--optimize**[ **+** &#124; **-** ]|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--preferreduilang:&lt;lang&gt;**| 指定慣用的輸出語言文化特性名稱（例如，es、ja-jp）。 |
|**--quiet**|隱藏F#對**stdout**資料流程的互動式輸出。|
|**--quotations-debug**|指定應該針對衍生自F#引號常值和反映定義的運算式發出額外的偵錯工具資訊。 系統會將偵錯工具F#資訊加入至運算式樹狀結構節點的自訂屬性。 請參閱程式[代碼引號](code-quotations.md)和[Expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3)。|
|**--readline**[ **+** &#124; **-** ]|在互動模式中啟用或停用 tab 鍵自動完成。|
|**--reference：&lt;filename&gt;**<br /><br />**-r：&lt;filename&gt;**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--shadowcopyreferences**[ **+** &#124; **-** ]|防止F#互動式進程鎖定參考。|
|**--simpleresolution**|使用以目錄為基礎的規則來解析元件參考，而不是 MSBuild 解析。|
|**--tailcalls**[ **+** &#124; **-** ]|啟用或停用 tail IL 指令，這會使堆疊框架重複用於尾遞迴函式。 這個選項預設為啟用。|
|**--targetprofile：&lt;字串&gt;**|指定這個元件的目標 framework 設定檔。 有效值為 mscorlib、netcore 或 netstandard。  預設值為 mscorlib。|
|**--使用：&lt;filename&gt;**|指示解譯器在啟動時使用指定的檔案做為初始輸入。|
|**--utf8output**|與 fsc 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--警告：&lt;警告層級&gt;**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--warnaserror**[ **+** &#124; **-** ]|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--warnaserror**[ **+** &#124; **-** ]: **&lt;int-list&gt;**|與**fsc**編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----|-----------|
|[編譯器選項](compiler-options.md)|描述適用于編譯器F# **fsc**的命令列選項。|
