---
title: "類型的值 &quot;&lt;typename1&gt;&quot;無法轉換成&quot;&lt;typename2&gt;&quot; （多重檔案參考） |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
dev_langs:
- VB
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: 9
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
ms.openlocfilehash: 732291ce9c4b83bb9fc7e83fbbc2a8da9748db59
ms.lasthandoff: 03/13/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>類型的值 '&lt;typename1&gt;'無法轉換成'&lt;typename2&gt;' （多重檔案參考）
類型的值 '\<typename1 >' 無法轉換成'\<typename2 >'。 型別不相符可能是因為混用的檔案參考 '\<filepath1 >' 在專案中'\<projectname1 >' 的檔案參考 '\<filepath2 >' 在專案中'\<projectname2 >'。 如果兩個組件相同，請嘗試更換這些參考，讓兩個參考都來自相同的位置。  
  
 其中一個專案可讓多個檔案參考的組件的情況下，編譯器無法保證，可以轉換成另一種類型。  
  
 每個檔案參考指定檔案路徑和名稱 （通常是 DLL 檔案） 專案的輸出檔案。 編譯器無法保證輸出檔，來自相同的來源，或其所代表的同一組件相同的版本。 因此，它無法保證在不同的參考型別都相同的型別，或其中甚至可以轉換成其他。  
  
 如果您知道參考的組件具有相同的組件識別，您可以使用單一檔案參考。 *「組件識別」* (assembly identity) 包含組件的名稱、版本、公開金鑰 (如果有) 和文化特性。 這是可唯一識別組件的資訊。  
  
 **錯誤識別碼︰** BC30961  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果參考的組件具有相同的組件識別，然後移除或取代其中一個檔案參考，讓它只包含單一檔案的參考。  
  
-   如果參考的組件不具有相同的組件識別，請變更您的程式碼，使它不會轉換成其他類型的其中一個型別。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的型別轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [NIB 如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
