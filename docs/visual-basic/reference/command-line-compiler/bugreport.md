---
title: -bugreport
ms.date: 03/08/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 766a4252fd77be95e2641239cba53a4d90e0cb1d
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-bugreport"></a>-bugreport
建立檔案錯誤報告時，您可以使用的檔案。  
  
## <a name="syntax"></a>語法  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`file`|必要。 將包含錯誤報告的檔案名稱。 將檔案名稱括在引號 ("") 如果名稱包含空格。|  
  
## <a name="remarks"></a>備註  
 下列資訊加入至`file`:  
  
-   在編譯中的所有原始程式檔的複本。  
  
-   在編譯中使用的編譯器選項的清單。  
  
-   您的編譯器、 通用語言執行平台，以及作業系統的版本資訊。  
  
-   編譯器輸出 (如果有的話)。  
  
-   此問題，會提示您輸入的描述。  
  
-   描述如何在您認為問題應該固定，會提示您輸入。  
  
 因為所有的原始程式檔的複本包含在`file`，您可能想要重新產生在最短的程式 （可能） 程式碼缺失。  
  
> [!IMPORTANT]
>  `-bugreport`選項會產生包含潛在的敏感資訊的檔案。 這包括目前的時間，編譯器版本[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]版本、 作業系統版本、 使用者名稱、 命令列引數，編譯器已執行，所有的原始程式碼，而且的二進位格式的任何參考的組件。 這個選項可以存取的伺服器端編譯的 Web.config 檔案中指定命令列選項[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]應用程式。 若要防止這個情況，修改 Machine.config 檔案，不允許使用者從伺服器上進行編譯。  
  
 如果此選項搭配`-errorreport:prompt`， `-errorreport:queue`，或`-errorreport:send`，和您的應用程式發生編譯器內部錯誤中的資訊`file`傳送給 Microsoft Corporation。 該資訊可協助 Microsoft 工程師找出錯誤的原因，而且可能有助於改善的下一個版本[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。 根據預設，會不傳送任何資訊給 Microsoft。 不過，當您編譯應用程式使用`-errorreport:queue`，預設會啟用它，應用程式收集的錯誤報表。 然後，當電腦的系統管理員登入時，錯誤報告系統就會顯示快顯視窗，可讓系統管理員以轉寄給 Microsoft 報告任何錯誤發生在登入。  
  
> [!NOTE]
>  `/bugreport`選項不是從 Visual Studio 開發環境中使用，則可以使用只有當您編譯從命令列。  
  
## <a name="example"></a>範例  
 下列範例會編譯`T2.vb`並放入檔案中的所有 bug 報告資訊`Problem.txt`。  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-偵錯 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [securityPolicy （ASP.NET 設定結構描述） 的 trustLevel 項目](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)
