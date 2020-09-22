---
title: Friend 組件參考 <reference> 無效
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 72c030d18d5339908c5088e104f6a8ad3e76943b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874095"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>Friend 組件參考 \<reference> 無效

Friend 元件參考 \<reference> 無效。 以強式名稱簽署的組件必須在其 InternalsVisibleTo 宣告中指定公開金鑰。  
  
 傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性（attribute）的元件名稱會識別強式名稱的元件，但不包含屬性（ `PublicKey` attribute）。  
  
 **錯誤識別碼：** BC31535  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 判斷強式名稱 friend 元件的公開金鑰。 使用屬性，將公開金鑰納入傳遞給屬性函式的元件名稱中 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `PublicKey` 。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.AssemblyName>
- [Friend 元件](../../../standard/assembly/friend.md)
