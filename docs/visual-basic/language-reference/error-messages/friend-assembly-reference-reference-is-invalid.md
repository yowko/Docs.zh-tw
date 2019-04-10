---
title: Friend 組件參考 <reference> 無效
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 0c1526e32ddc64cb4124c6f8205d58deef911dd6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298990"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>Friend 組件參考\<參考 > 無效
Friend 組件參考\<參考 > 無效。 以強式名稱簽署的組件必須在其 InternalsVisibleTo 宣告中指定公開金鑰。  
  
 將組件名稱傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性建構函式識別是強式名稱組件，但它不包含`PublicKey`屬性。  
  
 **錯誤 ID:** BC31535  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 決定強式名稱的 friend 組件的公開金鑰。 包含公開金鑰，組件名稱的一部分傳遞至<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性建構函式使用`PublicKey`屬性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.AssemblyName>
- [Friend 組件](../../../standard/assembly/friend-assemblies.md)
