---
title: 類型等價和內嵌 interop 類型
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ce1285f64c6d50fea2d44b60773d949b673b1825
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="type-equivalence-and-embedded-interop-types"></a>類型等價和內嵌 interop 類型

從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，通用語言執行平台支援將 COM 類型的類型資訊直接內嵌到 Managed 組件，而不需要 Managed 組件從 Interop 組件取得 COM 類型的類型資訊。 因為內嵌類型資訊僅包含 Managed 組件實際所使用的類型和成員，所以兩個 Managed 組件可能對於相同的 COM 類型會有非常不同的檢視。 每個 Managed 組件有不同的 <xref:System.Type> 物件以代表其 COM 類型檢視。 通用語言執行平台支援介面、結構、列舉和委派等這些不同檢視之間的類型等價。

類型等價表示從一個 Managed 組件傳到另一個的 COM 物件，可以在接收的組件中轉換成適當的 Managed 類型。

> [!NOTE]
> 類型等價和內嵌 Interop 類型簡化了使用 COM 元件之應用程式和增益集的部署，因為不必與應用程式一起部署 Interop 組件。 共用 COM 元件的開發人員仍然必須建立主要 Interop 組件 (PIA)，如果他們想要舊版 .NET Framework 使用其元件的話。

## <a name="type-equivalence"></a>類型等價

 針對介面、結構、列舉和委派支援 COM 類型等價。 如果下列所有各項都為 true，COM 類型便視相等：

- 類型同時為介面，或同時為結構，或同時為列舉，或同時為委派。

- 類型具有相同的身分識別，如下一節中所述。

- 中所述，這兩種類型是否適合類型等價，[標示 COM 類型的類型等價](#marking-com-types-for-type-equivalence)> 一節。

### <a name="type-identity"></a>型別身分識別

當兩個類型的範圍和身分識別相符時，會判斷它們具有相同的身分識別；換句話說，如果它們都有 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性，且兩個屬性都有相符的 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 和 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> 屬性。 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 的比較不區分大小寫。

如果類型沒有 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性，或它具有未指定範圍和識別項的 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性，該類型仍可以視為等價，如下所示：

- 對於介面，會使用 <xref:System.Runtime.InteropServices.GuidAttribute> 的值而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> 屬性，而且會使用 <xref:System.Type.FullName%2A?displayProperty=nameWithType> 屬性 (也就是類型名稱，包括命名空間) 而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> 屬性。

- 對於結構、列舉和委派，會使用包含組件的 <xref:System.Runtime.InteropServices.GuidAttribute>而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 屬性，而且會使用 <xref:System.Type.FullName%2A?displayProperty=nameWithType> 屬性，而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> 屬性。

### <a name="marking-com-types-for-type-equivalence"></a>標記類型等價的 COM 型別

 您可以將類型標記為適合類型等價，有兩種方法：

- 將 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性套用至該類型。

- 讓類型成為 COM 匯入類型。 如果介面具有 <xref:System.Runtime.InteropServices.ComImportAttribute> 屬性，便是 COM 匯入類型。 如果定義介面、結構、列舉或委派所在的組件具有 <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> 屬性，便是 COM 匯入類型。

## <a name="see-also"></a>另請參閱

<xref:System.Type.IsEquivalentTo%2A>  
[在 Managed 程式碼中使用 COM 類型](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))  
[匯入類型程式庫做為組件](importing-a-type-library-as-an-assembly.md)  
