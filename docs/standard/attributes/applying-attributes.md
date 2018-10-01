---
title: 套用屬性
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d28da0c788d40222ccd689807d6e51f66b4ce78
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2018
ms.locfileid: "47216706"
---
# <a name="applying-attributes"></a>套用屬性
使用下列流程將屬性套用至程式碼的元素。  
  
1.  定義新屬性，或從 .NET Framework 匯入屬性的命名空間以使用現有的屬性。  
  
2.  將屬性放在緊接於程式碼元素前面，以套用屬性。  
  
     每個語言有其自己的屬性語法。 在 C++ 和 C# 中，屬性以方括弧括住，而且與元素之間以空白字元隔開，其中可包含分行符號。 在 Visual Basic 中，屬性以角括弧括住，而且必須在相同的邏輯行。如果想要分行符號，可以使用行接續字元。
  
3.  指定屬性的位置參數和具名參數。  
  
     位置參數是必要的，而且必須位於任何具名參數前面。它們對應至屬性的其中一個建構函式的參數。 具名參數是選擇性，對應至屬性的讀寫屬性。 在 C++ 和 C# 中，指定每一個選擇性參數的 `name`=`value`，其中 `name` 是屬性的名稱。 在 Visual Basi 中，指定 `name`:=`value`。  
  
 當您編譯程式碼時，屬性會發出至中繼資料，並透過執行階段反映服務，提供給通用語言執行平台及任何自訂工具或應用程式使用。  
  
 依照慣例，所有屬性名稱的結尾都是 Attribute。 不過，有幾種以 Visual Basic 和 C# 等執行階段為目標的語言，並不需要您指定屬性的全名。 例如，如果您想要初始化 <xref:System.ObsoleteAttribute?displayProperty=nameWithType>，則只需要將其參考為**已淘汰**。  
  
## <a name="applying-an-attribute-to-a-method"></a>將屬性套用至方法  
 下列程式碼範例示範如何宣告 **System.ObsoleteAttribute**，將程式碼標記為已淘汰。 `"Will be removed in next version"` 字串會傳遞至屬性。 當呼叫這個屬性所描述的程式碼時，屬性會產生編譯器警告來顯示傳遞的字串。  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a>在組件層級套用屬性  
 如果您想要在組件層級套用屬性，請使用 **assembly** 關鍵字 (在 Visual Basic 中為 `Assembly`)。 下列程式碼顯示在組件層級套用的 **AssemblyTitleAttribute**。  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 套用此屬性時，字串 `"My Assembly"` 會放在檔案的中繼資料部分中的組件資訊清單。 您可以使用 [MSIL 反組譯工具 (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 或建立自訂程式擷取屬性，以檢視屬性。  
  
## <a name="see-also"></a>另請參閱

- [屬性](../../../docs/standard/attributes/index.md)  
- [擷取儲存於屬性中的資訊](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)  
- [概念](/cpp/windows/attributed-programming-concepts)  
- [屬性](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
