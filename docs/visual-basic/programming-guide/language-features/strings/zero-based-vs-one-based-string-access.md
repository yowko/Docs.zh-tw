---
title: 以零為基底的與以一為基底的字串存取
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 91d3fb9d7bfdf3d5af27fc6499583640946a802f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072284"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Visual Basic 中以零起始與以一起始的字串存取之比較

本主題將比較 Visual Basic 和 .NET Framework 如何提供字串中字元的存取權。 .NET Framework 一律以零為基底的方式存取字串中的字元，而 Visual Basic 提供以零為基礎和以一為基礎的存取，視函式而定。  
  
## <a name="one-based"></a>以一為基礎  

 如需以一個為基礎 Visual Basic 函式的範例，請考慮函式 `Mid` 。 它會採用引數，指出子字串開始的字元位置，從位置1開始。 .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法會使用字串中要開始子字串的字元索引，從位置0開始。 因此，如果您的字串為 "ABCDE"，則個別字元的編號為1、2、3、4、5，以與函式搭配使用 `Mid` ，但是0，1，2，3，4則用於 <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法。  
  
## <a name="zero-based"></a>以零為基底  

 如需以零為基底的 Visual Basic 函式的範例，請考慮使用 `Split` 函數。 它會分割字串，並傳回包含子字串的陣列。 .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> 方法也會分割字串，並傳回包含子字串的陣列。 因為函式 `Split` 和 <xref:System.String.Split%2A> 方法會傳回 .NET Framework 陣列，所以它們必須以零為基底。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic 中的字串簡介](introduction-to-strings.md)
