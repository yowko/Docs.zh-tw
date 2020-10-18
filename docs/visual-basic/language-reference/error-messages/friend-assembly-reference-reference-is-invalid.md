---
title: Friend 組件參考 <reference> 無效
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: a42dd99ffaa06dce4823ce5d022fac02ae99c6bd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160707"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a>BC31535： Friend 元件參考 \<reference> 無效

Friend 元件參考 \<reference> 無效。 以強式名稱簽署的組件必須在其 InternalsVisibleTo 宣告中指定公開金鑰。

 傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性（attribute）的元件名稱會識別強式名稱的元件，但不包含屬性（ `PublicKey` attribute）。

 **錯誤識別碼：** BC31535

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 判斷強式名稱 friend 元件的公開金鑰。 使用屬性，將公開金鑰納入傳遞給屬性函式的元件名稱中 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `PublicKey` 。

## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.AssemblyName>
- [Friend 元件](../../../standard/assembly/friend.md)
