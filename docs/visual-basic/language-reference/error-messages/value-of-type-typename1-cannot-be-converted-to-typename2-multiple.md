---
title: 型別的值&#39; &lt;typename1&gt; &#39;無法轉換成&#39; &lt;2>&gt; &#39; （多個檔案參考）
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 41c18160be9b546f8b525376fa06bc0eca6c117a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>型別的值&#39; &lt;typename1&gt; &#39;無法轉換成&#39; &lt;2>&gt; &#39; （多個檔案參考）
類型的值 '\<typename1 >' 無法轉換成'\<2> >'。 類型不符的情況可能是因為混用了檔案參考 '\<filepath1 >' 在專案中'\<projectname1 >' 的檔案參考 '\<filepath2 >' 在專案'\<專案名稱 2> >'。 如果兩個組件相同，請嘗試更換這些參考，讓兩個參考都來自相同的位置。  
  
 專案位置會一個以上的檔案參考的組件的情況下，編譯器無法保證，可以轉換成另一種類型。  
  
 每個檔案參考指定檔案路徑和名稱的專案 （通常是 DLL 檔案） 的輸出檔。 編譯器無法保證輸出檔，來自相同的來源，或它們代表相同的版本相同組件。 因此，它無法保證不同的參考中的類型為相同類型，或甚至一可轉換成另。  
  
 如果您知道參考的組件具有相同的組件識別，您可以使用單一檔案參考。 *「組件識別」* (assembly identity) 包含組件的名稱、版本、公開金鑰 (如果有) 和文化特性。 這是可唯一識別組件的資訊。  
  
 **錯誤 ID:** BC30961  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果參考的組件具有相同的組件識別，然後移除或取代其中一個檔案的參考，以便只包含單一檔案的參考。  
  
-   如果參考的組件不會有相同的組件識別，然後變更您的程式碼，使它不會轉換成其他類型的其中一個型別。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的型別轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)  
 
