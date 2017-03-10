---
title: "泛型和反映 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "泛型 [C#], 反映"
  - "反映 [C#], 泛型類型"
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 泛型和反映 (C# 程式設計手冊)
由於 Common Language Runtime \(CLR\) 可在執行階段存取泛型型別資訊，因此您可以使用反映取得泛型型別的相關資訊，方法和取得非泛型型別的資訊相同。  如需詳細資訊，請參閱 [執行階段中的泛型](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)。  
  
 [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong-md.md)] 中的 <xref:System.Type> 類別中加入了數個新成員，使泛型型別也能產生執行階段資訊。  如需使用這些方法和屬性的詳細資訊，請參閱這些類別的文件。<xref:System.Reflection.Emit> 命名空間也包含支援泛型的新成員。  請參閱 [如何：使用反映發出定義泛型類型](../Topic/How%20to:%20Define%20a%20Generic%20Type%20with%20Reflection%20Emit.md)。  
  
 如需泛型反映中所使用之規範的恆成立條件清單，請參閱 <xref:System.Type.IsGenericType%2A> 屬性的備註。  
  
|System.Type 成員名稱|描述|  
|----------------------|--------|  
|<xref:System.Type.IsGenericType%2A>|如果型別是泛型就傳回 true。|  
|<xref:System.Type.GetGenericArguments%2A>|傳回代表提供給建構之型別的型別引數，或是泛型型別定義之型別參數的 `Type` 物件陣列。|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|傳回目前建構之型別的基礎泛型型別定義。|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|傳回由 `Type` 物件組成的陣列，這些物件代表對目前泛型型別參數所設下的條件約束。|  
|<xref:System.Type.ContainsGenericParameters%2A>|如果型別或是其封入之任何型別或方法中，包含尚未提供之特定型別的型別參數，就傳回 true。|  
|<xref:System.Type.GenericParameterAttributes%2A>|取得描述目前泛型型別參數之特殊條件約束的 `GenericParameterAttributes` 旗標組合。|  
|<xref:System.Type.GenericParameterPosition%2A>|針對代表型別參數的 `Type` 物件，取得宣告型別參數之泛型型別定義或泛型方法定義中，型別參數清單內的型別參數位置。|  
|<xref:System.Type.IsGenericParameter%2A>|取得指出目前 `Type` 是否表示泛型型別或方法定義之型別參數的值。|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|取得指出目前 <xref:System.Type> 是否代表泛型型別定義，以便建構其他泛型型別的值。  如果型別代表泛型型別的定義，就傳回 true。|  
|<xref:System.Type.DeclaringMethod%2A>|傳回定義目前泛型型別參數的泛型方法，如果泛型方法並未定義，型別參數就是 null。|  
|<xref:System.Type.MakeGenericType%2A>|取代目前泛型型別定義之型別參數的型別陣列項目，並傳回代表產生之建構型別的 <xref:System.Type> 物件。|  
  
 此外，<xref:System.Reflection.MethodInfo> 類別中會加入新成員，使泛型方法也能產生執行階段資訊。  請參閱不區分條件之清單的 <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> 屬性備註，以得知用來反映泛型方法的詞彙。  
  
|System.Reflection.MemberInfo 成員名稱|描述|  
|---------------------------------------|--------|  
|<xref:System.Reflection.MethodInfo.IsGenericMethod%2A>|如果方法是泛型就傳回 true。|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|傳回 Type 物件陣列，以代表建構之泛型方法的型別引數或泛型方法定義的型別參數。|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|傳回目前建構之方法的基礎泛型方法定義。|  
|<xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A>|如果方法或是其封入之任何型別中包含尚未提供之特定型別的型別參數，就傳回 true。|  
|<xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A>|如果目前 <xref:System.Reflection.MethodInfo> 代表泛型方法的定義就傳回 true。|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|用型別陣列的元素取代目前泛型方法定義的型別參數，並傳回表示所得結果建構方法的 <xref:System.Reflection.MethodInfo> 物件。|  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型](../../../csharp/programming-guide/generics/index.md)   
 [反映和泛用類型](../Topic/Reflection%20and%20Generic%20Types.md)   
 [泛型](../Topic/Generics%20in%20the%20.NET%20Framework.md)