---
title: "類型的值 &quot;&lt;typename1&gt;&quot;無法轉換成&quot;&lt;typename2&gt;&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
dev_langs:
- VB
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 12
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
ms.openlocfilehash: c973d5e2aa03d423e1dea8053946172655f08490
ms.lasthandoff: 03/13/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>類型的值 '&lt;typename1&gt;'無法轉換成'&lt;typename2&gt;'
類型的值 '\<typename1 >' 無法轉換成'\<typename2 >'。 型別不相符可能是因為混用了檔案參考和組件的專案參考 '\<assemblyname >'。 請嘗試更換檔案參考 '\<filepath >' 在專案中'\<projectname1 >' 的專案參考 '\<projectname2 >'。  
  
 專案參考和檔案參考專案可讓的情況下，編譯器無法保證，可以轉換成另一種類型。  
  
 下列虛擬程式碼將說明可能產生此錯誤的情況。  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 專案`P1`會透過專案間接專案參考`P2`專案`P3`，以及也直接檔案參考`P3`。 宣告`commonObject`使用的檔案參考`P3`，而呼叫`P2.getCommonClass`會使用專案參考`P3`。  
  
 這種情況的問題是檔案參考指定檔案路徑和名稱的輸出檔`P3`(通常 p3.dll)，在專案參考中找到原始碼專案時 (`P3`) 的專案名稱。 因此，編譯器無法保證類型`P3.commonClass`來自相同的原始程式碼，透過兩個不同的參考。  
  
 通常發生這種情況在混合檔案參考和專案的參考時。 在上圖中，問題就不會發生如果`P1`所做的直接專案參考`P3`而非檔案參考。  
  
 **錯誤識別碼︰** BC30955  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   變更專案參考的檔案參考。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的型別轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [NIB 如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
