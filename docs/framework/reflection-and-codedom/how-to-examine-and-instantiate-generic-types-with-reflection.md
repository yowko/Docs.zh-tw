---
title: "如何：使用反映檢視和執行個體化泛型類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 27b6315b30c27d0902d34a013c6cb6c6072dffe7
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：使用反映檢視和執行個體化泛型類型
取得泛型型別相關資訊的方式，與取得其他型別的資訊一樣：檢查表示泛型型別的 <xref:System.Type> 物件。  基本的差異在於泛型型別有一個 <xref:System.Type> 物件清單，其表示它的泛型型別參數。  本章節中的第一個程序會檢查泛型型別。  
  
 您可以將型別引數繫結到泛型型別定義的型別參數，藉以建立表示建構的型別之 <xref:System.Type> 物件。  第二個程序將示範如何進行這個處理。  
  
### 若要檢查泛型型別和它的型別參數  
  
1.  取得表示此泛型型別的 <xref:System.Type> 執行個體。  在下列程式碼中，會使用 C\# `typeof` 運算子 \(Visual Basic 中為 `GetType`，Visual C\+\+ 中為 `typeid`\) 取得此型別。  請參閱 <xref:System.Type> 類別主題，以了解取得 <xref:System.Type> 物件的其他方式。  請注意此程序的其餘部分中，此型別會包含在名為 `t` 的方法參數中。  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2.  使用 <xref:System.Type.IsGenericType%2A> 屬性來判斷此型別是否為泛型，並使用 <xref:System.Type.IsGenericTypeDefinition%2A> 屬性來判斷此型別是否為泛型型別定義。  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3.  使用 <xref:System.Type.GetGenericArguments%2A> 方法取得包含泛型型別引數的陣列。  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4.  使用 <xref:System.Type.IsGenericParameter%2A> 屬性，針對每一個型別引數判斷它是否為型別參數 \(例如，在泛型型別定義中\)，或是否為已指定給型別參數的型別 \(例如，在建構的型別中\)。  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5.  在型別系統中，泛型型別參數是由 <xref:System.Type> 的執行個體所表示，就如同一般型別一樣。  下列程式碼將顯示表示泛型型別參數的 <xref:System.Type> 物件之名稱和參數位置；  參數位置在這裡並不是重要的資訊，當您正在檢查當做另一個泛型型別之型別引數使用的型別參數時，它才會比較重要。  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6.  使用 <xref:System.Type.GetGenericParameterConstraints%2A> 方法來取得單一陣列中的所有條件約束，以判斷泛型型別參數的基底型別條件約束和介面條件約束。  不保證條件約束一定會以任何特定的順序出現。  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7.  使用 <xref:System.Type.GenericParameterAttributes%2A> 屬性來探索型別參數上的特殊條件約束，例如，要求它必須是參考型別。  這個屬性也包含了表示變異數的值，您可以如下列程式碼中所示加以遮蔽。  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8.  特殊條件約束的屬性 \(Attribute\) 為旗標，而代表沒有特殊條件約束的同一旗標 \(<xref:System.Reflection.GenericParameterAttributes?displayProperty=fullName>\) 也用來代表沒有 Covariance 或 Contravariance。  因此，若要測試這些條件中的任何一項，您必須使用適當的遮罩。  在這種情況下，請使用 <xref:System.Reflection.GenericParameterAttributes?displayProperty=fullName> 隔離特殊條件約束旗標。  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## 建構泛型型別的執行個體  
 泛型型別就像是樣板一樣，  除非您為它的泛型型別參數指定真實的型別，否則將無法建立它的執行個體。  若要在執行階段使用反映 \(Reflection\) 進行這項處理，必須使用 <xref:System.Type.MakeGenericType%2A> 方法。  
  
#### 若要建構泛型型別的執行個體  
  
1.  取得表示泛型型別的 <xref:System.Type> 物件。  下列程式碼會以兩個不同方式取得泛型型別 <xref:System.Collections.Generic.Dictionary%602>：將 <xref:System.Type.GetType%28System.String%29?displayProperty=fullName> 方法多載與描述此型別的字串一起使用，以及呼叫建構的型別 `Dictionary\<String, Example>` \(Visual Basic 中為 `Dictionary(Of String, Example)`\) 上的 <xref:System.Type.GetGenericTypeDefinition%2A> 方法。  <xref:System.Type.MakeGenericType%2A> 方法需要泛型型別定義。  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2.  建構型別引數陣列來替代型別參數，  此陣列必須包含正確的 <xref:System.Type> 物件數目，且這些物件的出現順序必須與在型別參數清單中的順序相同。  在此情況下，索引鍵 \(第一個型別參數\) 具有型別 <xref:System.String>，且字典中的值會是名為 `Example` 的類別之執行個體。  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3.  呼叫 <xref:System.Type.MakeGenericType%2A> 方法，將型別引數繫結到型別參數，並建構此型別。  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4.  使用 <xref:System.Activator.CreateInstance%28System.Type%29> 方法多載來建立建構的型別之物件。  下列程式碼會將 `Example` 類別的兩個執行個體儲存到產生的 `Dictionary<String, Example>` 物件中。  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## 範例  
 下列程式碼範例會定義 `DisplayGenericType` 方法來檢查用於程式碼中的泛型型別定義和建構的型別，並顯示其資訊。  `DisplayGenericType` 方法會示範如何使用 <xref:System.Type.IsGenericType%2A>、<xref:System.Type.IsGenericParameter%2A> 和 <xref:System.Type.GenericParameterPosition%2A> 屬性及 <xref:System.Type.GetGenericArguments%2A> 方法。  
  
 此範例也會定義 `DisplayGenericParameter` 方法來檢查泛型型別參數，並顯示其條件約束。  
  
 此程式碼範例會定義一組測試型別 \(包括可說明型別參數條件約束的泛型型別\)，以及示範如何顯示與這些型別有關的資訊。  
  
 此範例會從 <xref:System.Collections.Generic.Dictionary%602> 類別建構型別，透過的方式是建立型別引數的陣列，以及呼叫 <xref:System.Type.MakeGenericType%2A> 方法。  程式會將使用 <xref:System.Type.MakeGenericType%2A> 建構的 <xref:System.Type> 物件與使用 `typeof` \(Visual Basic 中為 `GetType`\) 取得之 <xref:System.Type> 物件相比較，以示範兩者是相同的。  同樣地，程式會使用 <xref:System.Type.GetGenericTypeDefinition%2A> 方法來取得建構之型別的泛型型別定義，並將它與表示 <xref:System.Collections.Generic.Dictionary%602> 類別的 <xref:System.Type> 物件相比較。  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## 編譯程式碼  
  
-   此程式碼含有進行編譯所需的 C\# `using` 陳述式 \(Visual Basic 中的 `Imports`\)。  
  
-   不需要其他的組件參考。  
  
-   使用 csc.exe、vbc.exe 或 cl.exe 在命令列編譯程式碼。  若要在 Visual Studio 中編譯程式碼，請將程式碼放在主控台應用程式專案範本中。  
  
## 請參閱  
 <xref:System.Type>   
 <xref:System.Reflection.MethodInfo>   
 [反映和泛用類型](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)   
 [檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)   
 [泛型](../../../docs/standard/generics/index.md)

