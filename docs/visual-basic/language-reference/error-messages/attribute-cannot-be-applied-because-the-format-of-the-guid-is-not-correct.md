---
title: "&quot;&lt;屬性&gt;&quot; 無法套用，因為 GUID 的格式 &quot;&lt;數目&gt;&quot; 不是正確 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32500
- bc32500
dev_langs:
- VB
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 10
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
ms.openlocfilehash: f22f9ecd63582e2a346702919cf9154819b8eb0e
ms.lasthandoff: 03/13/2017

---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>'&lt;屬性&gt;' 無法套用，因為 GUID 的格式 '&lt;數目&gt;' 不正確
A`COMClassAttribute`屬性區塊中指定的全域唯一識別碼 (GUID) guid 不符合成適當格式。 `COMClassAttribute`使用 Guid 來唯一識別類別、 介面和建立事件。  
  
 GUID 由 16 個位元組組成，前八位是數字，後八位是二進位。 它由 Microsoft 公用程式，例如 uuidgen.exe 所產生，並保證是唯一的時間和空間內。  
  
 **錯誤識別碼︰** BC32500  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  判斷正確的 GUID 或需要識別的 COM 物件的 Guid。  
  
2.  請確定正確複製要呈現給 `COMClassAttribute` 屬性區塊的 GUID 字串。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Guid></xref:System.Guid>   
[屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)


