---
title: 作法：使用反映取得類型和成員資訊
description: 瞭解如何使用 system.string 命名空間，透過反映取得類型和成員資訊。
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 771917bb2ae5cae56c775ae23119d5eda9701df1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266320"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>作法：使用反映取得類型和成員資訊

<xref:System.Reflection>命名空間包含許多方法，可取得類型和其成員的相關資訊。 本文將示範其中一種方法 <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> 。 如需詳細資訊，請參閱 [反映總覽](reflection.md)。
  
## <a name="example"></a>範例

下列範例會使用反映來取得類型和成員資訊：

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>另請參閱

- [具有應用程式域的程式](../app-domains/application-domains.md#programming-with-application-domains)
- [反射](reflection.md)
- [使用應用程式域](../app-domains/use.md)
