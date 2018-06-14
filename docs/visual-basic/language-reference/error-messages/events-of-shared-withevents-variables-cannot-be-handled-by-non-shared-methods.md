---
title: 共用 WithEvents 變數的事件不能由非共用的方法處理
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f61f4cd17b1bb3088117e0a0d91b186fd40db3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585167"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>共用 WithEvents 變數的事件不能由非共用的方法處理
宣告變數`Shared`修飾詞是共用的變數。 共用的變數會識別一個儲存位置。 宣告變數`WithEvents`變數所屬的類型，處理變數引發的事件集的判斷提示的修飾詞。 屬性值指派給變數時，建立由`WithEvents`宣告取消攔截任何現有的事件處理常式，並透過新的事件處理常式連結`Add`方法。  
  
 **錯誤 ID:** BC30594  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   宣告事件處理常式`Shared`。  
  
## <a name="see-also"></a>另請參閱  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
