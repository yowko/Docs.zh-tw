---
title: "/warnaserror (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 28f232b1ad8200455550f2f4c1204818c8b143ab
ms.lasthandoff: 03/13/2017

---
# <a name="warnaserror-visual-basic"></a>/warnaserror (Visual Basic)
讓編譯器將第一個出現的警告視為錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|+ &#124; -|選擇項。 根據預設，`/warnaserror-`是生效; 警告不會防止編譯器產生的輸出檔。 `/warnaserror`是相同的選項為`/warnaserror+`，會將警告視為錯誤。|  
|`numberList`|選擇項。 逗號分隔清單的警告編號的數字的`/warnaserror`選項會套用。 如果沒有警告指定 ID，`/warnaserror`選項會套用至所有警告。|  
  
## <a name="remarks"></a>備註  
 `/warnaserror`選項會將所有警告視為錯誤。 原本為警告而是會回報為錯誤報告的任何訊息。 編譯器會報告為警告的相同警告後續出現項目。  
  
 根據預設，`/warnaserror-`有效，會將只是告知性警告。 `/warnaserror`是相同的選項為`/warnaserror+`，會將警告視為錯誤。  
  
 如果您想只有少數的特定警告視為錯誤，您可以指定要視為錯誤的警告編號的逗號分隔清單。  
  
> [!NOTE]
>  `/warnaserror`選項不會控制如何顯示警告。 使用[/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)選項來停用警告。  
  
|若要設定所有警告視為錯誤，在 Visual Studio IDE 中 /warnaserror|  
|---|  
|1.在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [編譯]**** 索引標籤。<br />3.請確定**停用所有警告**未核取核取方塊。<br />4.檢查**將所有警告視為錯誤**核取方塊。|  
  
|若要設定特定的警告視為錯誤，在 Visual Studio IDE 中 /warnaserror|  
|---|  
|1.在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。<br />2.按一下 [編譯]**** 索引標籤。<br />3.請確定**停用所有警告**未核取核取方塊。<br />4.請確定**將所有警告視為錯誤**未核取核取方塊。<br />5.選取**錯誤**從**通知**應該視為錯誤的警告旁邊的資料行。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`，並指示編譯器將會顯示錯誤，它會尋找每個警告的第一個相符項目。  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`和未使用區域變數 (42024) 警告視為錯誤。  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [在 Visual Basic 中設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)
