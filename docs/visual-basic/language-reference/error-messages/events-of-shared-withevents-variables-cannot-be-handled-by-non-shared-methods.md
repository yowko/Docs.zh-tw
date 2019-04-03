---
title: 共用 WithEvents 變數的事件不能由非共用的方法處理
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 2b32043898986b3e3e68fab18c5f907843d7691c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838647"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>共用 WithEvents 變數的事件不能由非共用的方法處理
以宣告的變數`Shared`修飾詞是共用的變數。 共用的變數會識別一個儲存體位置。 以宣告的變數`WithEvents`修飾詞會判斷提示變數所屬的類型處理的變數會引發的事件集。 屬性時的值指派給變數時，已由`WithEvents`宣告會解除鎖定的任何現有的事件處理常式，並透過新的事件處理常式連結`Add`方法。  
  
 **錯誤 ID:** BC30594  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   宣告事件處理常式`Shared`。  
  
## <a name="see-also"></a>另請參閱

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
