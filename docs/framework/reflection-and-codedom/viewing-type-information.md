---
title: "檢視類型資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "反映, 檢視類型資訊"
  - "Type 物件"
  - "類型, 檢視類型資訊"
  - "檢視類型資訊"
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 檢視類型資訊
<xref:System.Type?displayProperty=fullName> 類別為反映的核心。  當反映要求時，Common Language Runtime 會為載入的型別建立 **Type**。  您可以使用 **Type** 物件的方法、欄位、屬性和巢狀類別，找出該型別的一切事項。  
  
 使用 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName> 或 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>，可以從尚未載入的組件取得 **Type** 物件，傳入型別名稱或您所需的型別。  使用 <xref:System.Type.GetType%2A?displayProperty=fullName> 可以從已載入的組件取得 **Type** 物件。  使用 <xref:System.Reflection.Module.GetType%2A?displayProperty=fullName> 和 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=fullName> 可取得模組 **Type** 物件。  
  
> [!NOTE]
>  如果要檢查及使用泛型型別和方法，請參閱[反映和泛用類型](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)與 [如何：使用反映檢視和執行個體化泛型類型](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)中提供的詳細資訊。  
  
 下列範例說明取得 <xref:System.Reflection.Assembly> 物件和組件模組的必要語法。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 下列範例示範從載入的組件取得 **Type** 物件。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 一旦您取得 **Type**，有許多方式可供您尋找關於該型別成員的資訊。  例如，您可以呼叫 <xref:System.Type.GetMembers%2A?displayProperty=fullName> 方法，取得描述目前型別每一個成員的 <xref:System.Reflection.MemberInfo> 物件陣列，以找出型別的所有成員。  
  
 您也可以使用 **Type** 類別上的方法，擷取一個或多個您按名稱指定的建構函式、方法、事件、欄位或屬性的資訊。  例如，<xref:System.Type.GetConstructor%2A?displayProperty=fullName> 會封裝目前類別的特定建構函式。  
  
 如果有 **Type**，便可以使用 <xref:System.Type.Module%2A?displayProperty=fullName> 屬性，取得封裝含有該型別模組的物件。  使用 <xref:System.Reflection.Module.Assembly%2A?displayProperty=fullName> 屬性，找出封裝含有模組組件的物件。  您可以取得組件，使用 <xref:System.Type.Assembly%2A?displayProperty=fullName> 屬性直接封裝型別。  
  
## System.Type 和 ConstructorInfo  
 下列程式碼範例說明如何列出類別的建構函式，在此例中為 <xref:System.String> 類別。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## MemberInfo、MethodInfo、FieldInfo 和 PropertyInfo  
 使用 <xref:System.Reflection.MemberInfo>、<xref:System.Reflection.MethodInfo>、<xref:System.Reflection.FieldInfo> 或 <xref:System.Reflection.PropertyInfo> 物件，取得型別的方法、屬性、事件和欄位的資訊。  
  
 下列範例使用 **MemberInfo** 列出 **System.IO.File** 類別中成員的數目，並使用 [System.Type.IsPublic](frlrfSystemTypeClassIsPublicTopic) 屬性判斷類別的可視性。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 下列範例檢查指定成員的型別。  它執行 **MemberInfo** 類別成員上的反映，並列出它的型別。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 下列程式碼範例使用所有的 Reflection **\*Info** 類別，連同 <xref:System.Reflection.BindingFlags>，列出指定類別的所有成員 \(建構函式、欄位、屬性、事件和方法\)，並將成員區分為靜態和執行個體分類。  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## 請參閱  
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