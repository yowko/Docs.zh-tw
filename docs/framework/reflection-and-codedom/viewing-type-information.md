---
title: "檢視類型資訊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6b7225aeca9bf605f47dcc5a8430cdf1fb12d410
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="viewing-type-information"></a>檢視類型資訊
<xref:System.Type?displayProperty=fullName> 類別是反映的核心。 Common Language Runtime 會在反映提出要求時，建立載入類型的**類型**。 您可以使用**類型**物件的方法、欄位、屬性和巢狀類別，找出有關該類型的所有資訊。  
  
 使用 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName> 或 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>，從尚未載入、但以類型名稱或您想要的類型名稱傳遞的組件中，取得**類型**物件。 使用<xref:System.Type.GetType%2A?displayProperty=fullName>取得**類型**已載入的組件的物件。 使用 <xref:System.Reflection.Module.GetType%2A?displayProperty=fullName> 和 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=fullName> 取得模組**類型**物件。  
  
> [!NOTE]
>  如果您想要檢查和操作泛型型別和方法，請參閱[反映和泛用型別](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)提供的其他資訊，以及[如何：使用反映檢查和具現化泛型型別](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)。  
  
 下例示範為組件取得 <xref:System.Reflection.Assembly> 物件和模組的必要語法。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)] [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)] [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 下例示範從載入的組件中取得**類型**物件。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)] [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)] [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 一旦取得**類型**，就有許多方式可以探索該類型成員的相關資訊。 例如，您可以呼叫 <xref:System.Type.GetMembers%2A?displayProperty=fullName> 方法找出類型的所有成員，它會取得 <xref:System.Reflection.MemberInfo> 物件的陣列，描述目前類型的每一個成員。  
  
 您也可以對**類型**類別使用方法，擷取按名稱指定的一或多個建構函式、方法、事件、欄位或屬性的相關資訊。 例如，<xref:System.Type.GetConstructor%2A?displayProperty=fullName> 會封裝目前類別的特定建構函式。  
  
 如果您有**類型**，您可以使用 <xref:System.Type.Module%2A?displayProperty=fullName> 屬性，取得封裝模組的物件，而此模組包含該類型。 使用 <xref:System.Reflection.Module.Assembly%2A?displayProperty=fullName> 屬性找出封裝組件的物件，而此組件包含模組。 您可以使用 <xref:System.Type.Assembly%2A?displayProperty=fullName> 屬性直接取得封裝類型的組件。  
  
## <a name="systemtype-and-constructorinfo"></a>System.Type 和 ConstructorInfo  
 下例示範如何列出類別的建構函式，本例中為 <xref:System.String> 類別。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)] [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)] [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo、MethodInfo、FieldInfo 和 PropertyInfo  
 使用 <xref:System.Reflection.MemberInfo>、<xref:System.Reflection.MethodInfo>、<xref:System.Reflection.FieldInfo> 或 <xref:System.Reflection.PropertyInfo> 物件，取得類型方法、屬性、事件和欄位的相關資訊。  
  
 下例使用 **MemberInfo** 列出 **System.IO.File** 類別中的成員數目，並使用 <xref:System.Type.IsPublic%2A> 屬性判斷類別的可見度。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)] [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)] [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 下例會檢查指定的成員類型。 它會對 **MemberInfo** 類別的成員執行反映，列出其類型。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)] [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)] [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 下例使用所有反映 **\*Info** 類別與 <xref:System.Reflection.BindingFlags> 列出指定類別的所有成員 (建構函式、欄位、屬性、事件和方法)，將成員區分為靜態和執行個體類別。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)] [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)] [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection.BindingFlags>   
 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>   
 <xref:System.Type.GetType%2A?displayProperty=fullName>   
 <xref:System.Type.GetMembers%2A?displayProperty=fullName>   
 <xref:System.Type.GetFields%2A?displayProperty=fullName>   
 <xref:System.Reflection.Module.GetType%2A?displayProperty=fullName>   
 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=fullName>   
 <xref:System.Reflection.MemberInfo>   
 <xref:System.Reflection.ConstructorInfo>   
 <xref:System.Reflection.MethodInfo>   
 <xref:System.Reflection.FieldInfo>   
 <xref:System.Reflection.EventInfo>   
 <xref:System.Reflection.ParameterInfo>   
 [反映和泛用類型](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)

