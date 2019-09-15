---
title: Friend 組件參考 <reference> 無效
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 6eb46c6479adc69eaf65b34c69aa69977b4d62ef
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972397"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>Friend 元件參考\<參考 > 無效
Friend 元件參考\<參考 > 無效。 以強式名稱簽署的組件必須在其 InternalsVisibleTo 宣告中指定公開金鑰。  
  
 傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性（attribute）的元件名稱會識別強式名稱的元件，但不`PublicKey`包含屬性（attribute）。  
  
 **錯誤識別碼：** BC31535  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 判斷強式名稱 friend 元件的公開金鑰。 使用屬性，將公開金鑰包含在傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性（attribute）的元件名稱中。 `PublicKey`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.AssemblyName>
- [Friend 組件](../../../standard/assembly/friend.md)
