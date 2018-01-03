---
title: /warnaserror (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d472795affe0df098d1551daf51a2f0ae20723ba
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="warnaserror-visual-basic"></a>/warnaserror (Visual Basic)
可讓編譯器將第一個出現的警告視為錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|+ &#124; -|選擇性。 根據預設，`/warnaserror-`是作用中; 警告不會防止編譯器產生的輸出檔。 `/warnaserror`相同的選項為`/warnaserror+`，會導致警告視為錯誤。|  
|`numberList`|選擇性。 以逗號分隔清單的警告 ID 編號的`/warnaserror`選項會套用。 如果未不指定任何警告 ID，則`/warnaserror`選項會套用至所有警告。|  
  
## <a name="remarks"></a>備註  
 `/warnaserror`選項會將所有警告都視為錯誤。 原本為警告而是會回報為錯誤報告的任何訊息。 編譯器會報告為警告的相同警告後面出現。  
  
 根據預設，`/warnaserror-`生效，這會導致只是告知性警告。 `/warnaserror`相同的選項為`/warnaserror+`，會導致警告視為錯誤。  
  
 如果您想只有少數的特定警告視為錯誤，您可以指定要視為錯誤的警告編號的逗號分隔清單。  
  
> [!NOTE]
>  `/warnaserror`選項不會控制會顯示警告訊息。 使用[/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)選項以停用警告。  
  
|若要設定 /warnaserror 將所有警告視為錯誤，Visual Studio IDE 中|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.請確定**停用所有警告**未選取核取方塊。<br />4.請檢查**將所有警告視為錯誤**核取方塊。|  
  
|若要設定 /warnaserror 將特定警告視為錯誤，Visual Studio IDE 中|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。<br />2.按一下 [編譯] 索引標籤。<br />3.請確定**停用所有警告**未選取核取方塊。<br />4.請確定**將所有警告視為錯誤**未選取核取方塊。<br />5.選取**錯誤**從**通知**應該視為錯誤的警告旁邊的資料行。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`和指示編譯器將顯示的第一個找到的每個警告的錯誤。  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`和未使用本機變數 (42024) 警告視為錯誤。  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [在 Visual Basic 中設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)
