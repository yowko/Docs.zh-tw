---
title: 屬性或方法呼叫不能包含 private 物件的參考，也不可以當做引數或傳回值
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 67b0b50ecd6d7933d2aeea4556a8e261632e297a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646908"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>屬性或方法呼叫不能包含 private 物件的參考，也不可以當做引數或傳回值
可能導致本錯誤的原因包括：  
  
- 用戶端已叫用跨處理序元件的屬性或方法，並嘗試將 private 物件的參考傳遞為其中一個引數。  
  
- 跨處理序元件已在其用戶端上叫用回撥方法，並嘗試傳遞 private 物件的參考。  
  
- 跨處理序元件已嘗試將 private 物件的參考傳遞為所引發事件的引數。  
  
- 用戶端已嘗試將 private 物件參考指派給所處理事件的 `ByRef` 引數。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請移除參考。  
  
## <a name="see-also"></a>另請參閱

- [Private](../../../visual-basic/language-reference/modifiers/private.md)
