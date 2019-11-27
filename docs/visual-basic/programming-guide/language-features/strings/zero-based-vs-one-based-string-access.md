---
title: 以零為基底與以一為基底的字串存取
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 97e60038bc7ec0f030939d0980b786bffebcfb9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354293"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Visual Basic 中以零起始與以一起始的字串存取之比較
本主題比較 Visual Basic 和 .NET Framework 如何提供字串中字元的存取權。 .NET Framework 一律會以零為基底的方式存取字串中的字元，而 Visual Basic 提供以零為基底的存取，視函式而定。  
  
## <a name="one-based"></a>以一為基礎  
 如需以一為基礎 Visual Basic 函式的範例，請考慮使用 `Mid` 函數。 它會採用引數，指出子字串開始的字元位置，從位置1開始。 .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法會取得字串中的字元索引，其為子字串的開頭，從位置0開始。 因此，如果您有字串 "ABCDE"，則個別字元的編號為1、2、3、4、5以用於 `Mid` 函式，但0、1、2、3、4用於 <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法。  
  
## <a name="zero-based"></a>以零為基底  
 如需以零為基底的 Visual Basic 函式的範例，請考慮使用 `Split` 函數。 它會分割字串，並傳回包含子字串的陣列。 .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> 方法也會分割字串，並傳回包含子字串的陣列。 因為 `Split` 函式和 <xref:System.String.Split%2A> 方法會傳回 .NET Framework 的陣列，所以它們必須是以零為起始的。  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
