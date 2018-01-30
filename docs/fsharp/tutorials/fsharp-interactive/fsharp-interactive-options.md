---
title: "F# Interactive 選項"
description: "了解命令列選項支援 F # Interactive fsi.exe。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9f3e39b-ce6c-41ff-991f-0625f46441ae
ms.openlocfilehash: a9b36a12aa9ffcfa26ea50d72d018a25f5f65243
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2018
---
# <a name="f-interactive-options"></a>F# Interactive 選項

> [!NOTE]
本文目前僅描述 Windows 的體驗。  將會加以重新撰寫。

本主題描述支援 F # Interactive 命令列選項`fsi.exe`。 F # Interactive 接受許多相同的命令列選項為 F # 編譯器，但也可接受一些其他選項。

## <a name="using-f-interactive-for-scripting"></a>使用 F # Interactive 來編寫指令碼
F # Interactive， `fsi.exe`、 以互動方式，來啟動或從命令列執行指令碼啟動。 命令列語法

```
> fsi.exe [options] [ script-file [arguments] ]
```

F # 指令碼檔案的副檔名是`.fsx`。

## <a name="table-of-f-interactive-options"></a>F # Interactive 選項的資料表
下表摘要說明支援 F # Interactive 選項。 在命令列上或透過 Visual Studio IDE，您可以設定這些選項。 若要在 Visual Studio IDE 中設定這些選項，開啟**工具**功能表上，選取**選項...**，然後展開**F # 工具**節點，然後選取**F # Interactive**。

清單項目清單會出現在 F # Interactive 選項引數，其中以分號分隔 (`;`)。

|選項|描述|
|------|-----------|
|**--**|用來指示 F # Interactive 命令列引數其餘引數視為 F # 程式或指令碼，您可以存取程式碼中使用清單**fsi.commandlineargs 存取**。|
|**--checked**[**+**&#124;**-**]|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--codepage:&lt;int&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--crossoptimize**[**+**&#124;**-**]|啟用或停用跨模組最佳化。|
|**--debug**[**+**&#124;**-**]<br /><br />**--debug:**[**full**&#124;**pdbonly**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g:**[**full**&#124;**pdbonly**]|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--define:&lt;string&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--exec**|指示 F # interactive 結束之後載入檔案或執行命令列上指定的指令碼檔案。|
|**--fullpaths**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--gui**[**+**&#124;**-**]|啟用或停用 Windows Form 事件迴圈。 會啟用預設值。|
|**--help**<br /><br />**-?**|用來顯示命令列語法和每個選項的簡短描述。|
|**--lib:&lt;folder-list&gt;**<br /><br />**-I:&lt;folder-list&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--load:&lt;filename&gt;**|編譯指定的來源處的程式碼啟動，並將已編譯的 F # 建構載入到工作階段。 如果包含指令碼的指示詞，例如目標來源**#use**或**#load**，則您必須使用**-使用**或**#use**而不是**-載入**或**#load**。|
|**--mlcompatibility**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--noframework**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)|
|**--nologo**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--nowarn:&lt;warning-list&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--optimize**[**+**&#124;**-**]|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--quiet**|隱藏 F # Interactive 的輸出到**stdout**資料流。|
|**--quotations-debug**|指定的額外偵錯資訊應該發出對衍生自 F # 引號常值，而且反映定義的運算式。 偵錯資訊已加入至 F # 運算式樹狀結構節點的自訂屬性。 請參閱[程式碼引號](../../language-reference/code-quotations.md)和[Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3)。|
|**--readline**[**+**&#124;**-**]|啟用或停用在互動模式中的 tab 鍵自動完成。|
|**--reference:&lt;filename&gt;**<br /><br />**-r:&lt;filename&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--tailcalls**[**+**&#124;**-**]|啟用或停用造成可重複使用之結尾遞迴函式的堆疊框架結尾 IL 指令的使用。 這個選項預設為啟用。|
|**--use:&lt;filename&gt;**|會告知使用指定的檔案，在啟動做為初始輸入的直譯器。|
|**--utf8output**|Fsc.exe 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--warn:&lt;warning-level&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--warnaserror**[**+**&#124;**-**]|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|與相同**fsc.exe**編譯器選項。 如需詳細資訊，請參閱[編譯器選項](../../language-reference/compiler-options.md)。|

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----|-----------|
|[編譯器選項](../../language-reference/compiler-options.md)|描述對於 F # 編譯器，可用的命令列選項**fsc.exe**。|
