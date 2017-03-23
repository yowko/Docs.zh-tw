---
title: "&lt;訊息&gt;此錯誤也可能是因為混用了檔案參考和組件的專案參考 &quot;&lt;assemblyname&gt;&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
dev_langs:
- VB
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: a1806fd078fc05d966c718841e5b78c1323a43c2
ms.lasthandoff: 03/13/2017

---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;訊息&gt;此錯誤也可能是因為混用了檔案參考和組件的專案參考 '&lt;assemblyname&gt;'
\<訊息 > 這項錯誤也可能是因為混用了檔案參考和組件的專案參考 '\<assemblyname >。 在此情況下，請嘗試更換檔案參考 '\<assemblyfilename >' 在專案中'\<projectname1 >' 的專案參考 '\<projectname2 >'。  
  
 在專案中的程式碼存取屬於另一個專案，但您的方案組態不允許[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器來解析參考。  
  
 若要存取其他的組件中定義的型別[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器必須有該組件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤 ID︰** BC30971  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。  
  
2.  在專案屬性中，加入包含組件之專案的參考，此組件定義所使用的類型。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [宣告項目參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [NIB 如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB 如何︰ 修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [針對中斷參考進行疑難排解](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)
