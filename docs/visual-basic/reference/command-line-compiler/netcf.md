---
title: "/netcf |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- netcf
dev_langs:
- VB
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d8e2328eb5434ea0e73238709c429975ae29e6d0
ms.lasthandoff: 03/13/2017

---
# <a name="netcf"></a>/netcf
設定要以 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] 為目標的編譯器。  
  
## <a name="syntax"></a>語法  
  
```  
/netcf  
```  
  
## <a name="remarks"></a>備註  
 `/netcf`選項會使[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]目標的編譯器[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]而不是完整[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]。 目前只有在完整的語言功能[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]已停用。  
  
 `/netcf`選項設計來搭配[/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)。 停用的語言功能`/netcf`都是相同的語言功能不存在於目標檔案`/sdkpath`。  
  
> [!NOTE]
>  `/netcf`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。 `/netcf`時設定選項[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]載入裝置專案。  
  
 `/netcf`選項會變更下列語言功能︰  
  
-   [結束\<關鍵字 > 陳述式](../../../visual-basic/language-reference/statements/end-keyword-statement.md)關鍵字，終止程式執行時，會停用。 下列程式會編譯並執行，而無`/netcf`會在編譯階段失敗，但`/netcf`。  
  
     [!code-vb[VbVbalrCompiler #&34;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   晚期繫結在所有表單中，會停用。 可辨識晚期繫結的狀況發生時，會產生編譯時期錯誤。 下列程式會編譯並執行，而無`/netcf`會在編譯階段失敗，但`/netcf`。  
  
     [!code-vb[VbVbalrCompiler #&35;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   [自動](../../../visual-basic/language-reference/modifiers/auto.md)， [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)，和[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修飾詞會停用。 語法[宣告陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)陳述式也會修改成`Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`。 下列程式碼顯示的效果`/netcf`編譯。  
  
     [!code-vb[VbVbalrCompiler #&36;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   使用 Visual Basic 6.0 關鍵字中移除[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會產生不同的錯誤時`/netcf`用。 這會影響下列關鍵字的錯誤訊息︰  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a>範例  
 下列程式碼編譯`Myfile.vb`與[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]，使用 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本中的預設安裝目錄中找到[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]C 磁碟機上。 一般而言，您可使用的最新版本[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]。  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
