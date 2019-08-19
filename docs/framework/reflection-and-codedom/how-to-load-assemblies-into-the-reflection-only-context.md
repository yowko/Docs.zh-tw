---
title: 作法：將組件載入僅限反映的內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e22dcf7db5ec2c78a79e574604e0b39b4962727
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971849"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>作法：將組件載入僅限反映的內容

僅限反映的載入內容可讓您檢查針對其他平台或其他 .NET Framework 版本所編譯的組件。 只能檢查載入至此內容的程式碼，而無法執行。 這表示無法建立物件，因為無法執行建構函式。 因為無法執行程式碼，所以不會自動載入相依性。 如果您需要檢查它們，則必須自行載入。

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>將組件載入僅限反映的載入內容

1. 使用 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> 方法多載來載入組件並提供其顯示名稱，或 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 方法來載入組件並提供其路徑。 如果組件是二進位映像，請使用 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> 方法多載。

    > [!NOTE]
    > 您無法使用僅限反映的內容，從執行內容中的版本以外的 .NET Framework 版本載入 mscorlib.dll 版本。

2. 如果組件具有相依性，則 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> 方法不會載入它們。 如果您需要檢查它們，則必須自行載入。

3. 判斷是否使用組件的 <xref:System.Reflection.Assembly.ReflectionOnly%2A> 屬性，將組件載入僅限反映的內容。

4. 如果已將屬性套用至組件或組件中的類型，請使用 <xref:System.Reflection.CustomAttributeData> 類別來檢查這些屬性，確保不會嘗試在僅限反映的內容中執行程式碼。 使用 <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> 方法的適當多載來取得 <xref:System.Reflection.CustomAttributeData> 物件，這些物件代表套用至組件、成員、模組或參數的屬性。

    > [!NOTE]
    > 套用至組件或其內容的屬性可能定義於組件中，或可能定義於另一個載入僅限反映內容的組件中。 沒有方法事先知道定義屬性的位置。

## <a name="example"></a>範例

下列程式碼範例示範如何檢查套用至載入僅限反映內容之組件的屬性。

此程式碼範例會定義具有兩個建構函式和一個屬性 (property) 的自訂屬性 (attribute)。 屬性會套用至組件、組件中宣告的類型、類型的方法，以及方法的參數。 執行時，組件會將它自己載入僅限反映的內容，並顯示已套用至它以及它所含類型和成員之自訂屬性的相關資訊。

> [!NOTE]
> 為了簡化程式碼範例，組件會載入並檢查本身。 一般來說，您不會想要找到同時載入執行內容和僅限反映內容的相同組件。

[!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
[!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
[!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]

## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
