---
title: "&lt;訊息&gt;此錯誤也可能是因為混用了檔案參考和組件 &#39; 的專案參考&lt;assemblyname&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords: BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0fcbcc48928b1b03487f31930e3d14051ddd990a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;訊息&gt;此錯誤也可能是因為混用了檔案參考和組件 &#39; 的專案參考&lt;assemblyname&gt;&#39;
\<訊息 > 這個錯誤也可能是因為混用了檔案參考和組件的專案參考 '\<assemblyname >。 在此情況下，請嘗試更換的檔案參考 '\<assemblyfilename >' 在專案'\<projectname1 >' 的專案參考 '\<專案名稱 2> >'。  
  
 您專案中的程式碼會存取另一個專案的成員，但您的解決方案組態不允許 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器解析參考。  
  
 若要存取另一個組件中所定義的類型， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器必須有該組件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤 ID︰** BC30971  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。  
  
2.  在專案屬性中，加入包含組件之專案的參考，此組件定義所使用的類型。  
  
## <a name="see-also"></a>請參閱  
 [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)  
 [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)  
 [針對中斷參考進行疑難排解](/visualstudio/ide/troubleshooting-broken-references)
