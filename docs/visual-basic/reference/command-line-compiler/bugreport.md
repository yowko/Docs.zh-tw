---
title: "/bugreport |Microsoft 文件"
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
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: 22
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
ms.openlocfilehash: 9c64ec49d7e6842edbc0fed7407a34132a8f5a88
ms.lasthandoff: 03/13/2017

---
# <a name="bugreport"></a>/bugreport
建立時提出問題報告，您可以使用的檔案。  
  
## <a name="syntax"></a>語法  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`file`|必要項。 將包含錯誤報告的檔案名稱。 將檔案名稱括在引號 ("") 如果名稱包含空格。|  
  
## <a name="remarks"></a>備註  
 下列資訊加入至`file`:  
  
-   在編譯中的所有原始程式碼檔案的複本。  
  
-   編譯器選項編譯中使用的清單。  
  
-   您的編譯器、 通用語言執行平台，以及作業系統的版本資訊。  
  
-   編譯器輸出，如果有的話。  
  
-   問題，會提示您輸入的描述。  
  
-   描述如何在您認為問題應該固定，會提示您輸入。  
  
 因為所有原始程式檔的複本包含在`file`，您可能想要重現中最短的程式 （可能） 程式碼缺失。  
  
> [!IMPORTANT]
>  `/bugreport`選項會產生包含潛在的敏感資訊的檔案。 這包括目前的時間，編譯器版本[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]版本、 作業系統版本、 使用者名稱、 命令列引數執行編譯器，所有的原始碼與二進位格式的任何參考組件。 這個選項可以存取在伺服器端編譯程式的 Web.config 檔案中指定命令列選項[!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]應用程式。 若要避免這個問題，修改 Machine.config 檔案，不允許使用者在伺服器上進行編譯。  
  
 如果這個選項搭配`/errorreport:prompt`， `/errorreport:queue`，或`/errorreport:send`，且您的應用程式遇到內部編譯器錯誤中的資訊`file`傳送至 Microsoft Corporation。 這項資訊可協助 Microsoft 工程師找出錯誤的原因，而且可能有助於改善的下一個版本[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。 根據預設，任何資訊會不傳送給 Microsoft。 不過，當您編譯應用程式使用`/errorreport:queue`，預設會啟用它，應用程式會收集其錯誤報告。 然後，當電腦的系統管理員登入時，錯誤報告系統便會顯示快顯視窗，可讓系統管理員登入後，發生任何錯誤報告的 Microsoft 轉送給。  
  
> [!NOTE]
>  `/bugreport`選項不是從 Visual Studio 開發環境中使用; 其只當您編譯從命令列。  
  
## <a name="example"></a>範例  
 下列範例會編譯`T2.vb`，並將錯誤報告的所有資訊都放在檔案中`Problem.txt`。  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [（ASP.NET 設定結構描述） securityPolicy 的 trustLevel 項目](http://msdn.microsoft.com/en-us/729ab04c-03da-4ee5-86b1-be9d08a09369)
