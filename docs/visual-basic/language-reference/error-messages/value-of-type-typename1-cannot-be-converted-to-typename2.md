---
title: "類型 &#39; 的值&lt;typename1&gt;&#39; 無法轉換成 &#39;&lt;2>&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords: BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b583c4272dd6e964de99fb14d2795152c655f3aa
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>類型 &#39; 的值&lt;typename1&gt;&#39; 無法轉換成 &#39;&lt;2>&gt;&#39;
類型的值 '\<typename1 >' 無法轉換成'\<2> >'。 類型不符的情況可能是因為混用了檔案參考和組件的專案參考 '\<assemblyname >'。 請嘗試更換的檔案參考 '\<檔案路徑 >' 在專案中'\<projectname1 >' 的專案參考 '\<專案名稱 2> >'。  
  
 專案參考和檔案參考專案可讓的情況下，編譯器無法保證，可以轉換成另一種類型。  
  
 下列虛擬程式碼說明可能會產生此錯誤的情況。  
  
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
  
 專案`P1`會透過專案間接專案參考`P2`專案`P3`，以及也的檔案直接參考`P3`。 宣告`commonObject`會使用檔案參考`P3`，而呼叫`P2.getCommonClass`會使用專案參考`P3`。  
  
 這種情況的問題是檔案參考指定的檔案路徑和名稱的輸出檔案的`P3`(通常 p3.dll)，而專案參考找出來源專案 (`P3`) 的專案名稱。 因此，編譯器無法保證類型`P3.commonClass`來自相同的原始碼，透過這兩個不同的參考。  
  
 通常會發生這種情況在混合檔案參考和專案的參考時。 在上圖中，會發生問題如果`P1`進行直接的專案參考加入`P3`而非檔案參考。  
  
 **錯誤 ID:** BC30955  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   變更專案參考的檔案參考。  
  
## <a name="see-also"></a>請參閱  
 [在 Visual Basic 中的型別轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)  
 
