---
title: "/errorreport |Microsoft 文件"
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
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ebe5646256926f68a1a900b91c25a1768505785
ms.lasthandoff: 03/13/2017

---
# <a name="errorreport"></a>/errorreport
指定 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器報告編譯器內部錯誤的方式。  
  
## <a name="syntax"></a>語法  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>備註  
 此選項提供便利的方式來報告[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器內部錯誤 (ICE) [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Microsoft 小組。 根據預設，編譯器會將任何資訊傳送到 Microsoft。 不過，如果發生編譯器內部錯誤，此選項可讓您向 Microsoft 回報錯誤。 這項資訊可協助 Microsoft 工程師找出原因，而且可能有助於改善的下一個版本[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
 傳送報表的使用者的能力取決於電腦和使用者原則權限。  
  
 下表摘要說明的效果`/errorreport`選項。  
  
|選項|行為|  
|---|---|  
|`prompt`|如果發生編譯器內部錯誤，對話方塊隨即出現，讓您可以檢視編譯器所收集的確切資料。 您可以判斷是否有任何錯誤報表中的機密資訊，並決定是否要傳送給 Microsoft。 如果您決定要傳送，而且電腦和使用者原則設定可讓它，編譯器會將資料傳送給 Microsoft。|  
|`queue`|錯誤報告排入佇列。 當您登入系統管理員權限時，您可以在上次登入報告任何失敗 （將不會提示您要傳送報告的失敗一次以上每隔三天）。 這是預設行為時`/errorreport`未指定選項。|  
|`send`|如果發生編譯器內部錯誤，而且電腦和使用者原則設定可讓它，編譯器會將資料傳送給 Microsoft。<br /><br /> 選擇`/errorReport:send`會嘗試自動傳送給 Microsoft 的資訊時發生錯誤。 此選項取決於登錄中。 如需在登錄中設定適當的值的詳細資訊，請參閱[如何開啟自動錯誤報告在 Visual Studio 2008 命令列工具](http://go.microsoft.com/fwlink/?LinkID=184695)。|  
|`none`|發生內部編譯器錯誤時，它將不會收集或傳送到 Microsoft。|  
  
 編譯器會傳送資料，包括堆疊時的錯誤，通常包括一些原始程式碼。 如果`/errorreport`搭配[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)選項，則會傳送整個原始程式檔。  
  
 這個選項最適合搭配[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)選項，因為它可讓 Microsoft 工程師更輕鬆地重現錯誤。  
  
> [!NOTE]
>  `/errorreport`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。  
  
## <a name="example"></a>範例  
 下列程式碼會嘗試編譯`T2.vb`，而且如果編譯器遇到內部編譯器錯誤，它會提示您傳送錯誤報告給 Microsoft。  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
