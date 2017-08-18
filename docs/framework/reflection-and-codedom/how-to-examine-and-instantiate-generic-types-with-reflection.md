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
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>如何：使用反映檢視和執行個體化泛型類型
取得泛型型別相關資訊的方式和取得其他類型相關資訊的方式一樣：檢查代表泛型型別的 <xref:System.Type> 物件。 主要差異是泛型型別有代表其泛型型別參數的 <xref:System.Type> 物件清單。 本節的第一個程序是檢查泛型型別。  
  
 您可以將型別引數繫結至泛型型別定義的型別參數，建立代表建構類型的 <xref:System.Type> 物件。 第二個程序即示範此作業。  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>檢查泛型型別及其型別參數  
  
1.  取得表示泛型型別的 <xref:System.Type> 執行個體。 在下列程式碼中，類型是使用 C# `typeof` 運算子取得 (Visual Basic 為 `GetType`，Visual C++ 為 `typeid`)。 請參閱 <xref:System.Type> 類別主題了解取得 <xref:System.Type> 物件的其他方法。 請注意，在此程序的其餘部分中，類型是包含在名為 `t` 的方法參數中。  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]  [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]  [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2.  使用 <xref:System.Type.IsGenericType%2A> 屬性判斷類型是否為泛型，使用 <xref:System.Type.IsGenericTypeDefinition%2A> 屬性判斷類型是否為泛型型別定義。  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]  [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]  [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3.  使用 <xref:System.Type.GetGenericArguments%2A> 方法取得包含泛型型別引數的陣列。  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]  [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]  [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4.  每個型別引數都要使用 <xref:System.Type.IsGenericParameter%2A> 屬性判斷它是型別參數 (例如，在泛型型別定義中)，還是已針對型別參數指定的類型 (例如，在建構的類型中)。  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]  [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]  [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5.  在型別系統中，泛型型別參數是由 <xref:System.Type> 執行個體表示，就像一般的類型一 樣。 下列程式碼會顯示表示泛型型別參數之 <xref:System.Type> 物件的名稱和參數位置。 參數位置在此為一般的資訊，但當您檢查曾用為其他泛型型別之型別引數的型別參數時，它就很有意思了。  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]  [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]  [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6.  使用 <xref:System.Type.GetGenericParameterConstraints%2A> 方法取得單一陣列中的所有條件約束，來判斷泛型型別參數的基底類型條件約束和介面條件約束。 條件約束不保證任何特定順序。  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]  [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]  [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7.  使用 <xref:System.Type.GenericParameterAttributes%2A> 屬性探索型別參數上的特殊條件約束，例如需要它為參考型別。 屬性也包含代表差異的值，您可以關閉遮罩，如下列程式碼所示。  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]  [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]  [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8.  特殊條件約束屬性是旗標，而不代表任何特殊條件約束的相同旗標 (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=fullName>)，也不代表任何共變數或反變數。 因此，若要測試任一條件，您必須使用適當的遮罩。 本例使用 <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=fullName> 隔離特殊條件約束旗標。  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]  [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]  [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>建構泛型型別的執行個體  
 泛型型別就像範本。 除非指定其泛型型別參數的真實類型，否則無法建立它的執行個體。 若要在執行階段使用反映執行這項操作，需要 <xref:System.Type.MakeGenericType%2A> 方法。  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>建構泛型型別的執行個體  
  
1.  取得表示泛型型別的 <xref:System.Type> 物件。 下列程式碼以兩種方式取得泛型型別 <xref:System.Collections.Generic.Dictionary%602>：使用 <xref:System.Type.GetType%28System.String%29?displayProperty=fullName> 方法多載及描述類型的字串，以及在建構的類型 `Dictionary\<String, Example>`(Visual Basic 為 `Dictionary(Of String, Example)`) 上呼叫 <xref:System.Type.GetGenericTypeDefinition%2A> 方法。 <xref:System.Type.MakeGenericType%2A> 方法需要泛型型別定義。  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]  [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]  [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2.  建構型別引數陣列來替代型別參數。 陣列必須包含正確的 <xref:System.Type> 物件數，依型別參數清單中的出現順序排序。 本例中的索引鍵 (第一個型別參數) 類型是 <xref:System.String>，字典中的值則是名為 `Example` 的類別執行個體。  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]  [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]  [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3.  呼叫 <xref:System.Type.MakeGenericType%2A> 方法將型別引數繫結至型別參數，並建構類型。  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]  [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]  [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4.  使用 <xref:System.Activator.CreateInstance%28System.Type%29> 方法多載來建立建構類型的物件。 下列程式碼會將 `Example` 類別的兩個執行個體儲存在產生的 `Dictionary<String, Example>` 物件中。  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]  [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]  [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>範例  
 下列程式碼範例會定義 `DisplayGenericType` 方法，檢查程式碼中的泛型型別定義和建構的類型，並顯示其相關資訊。 `DisplayGenericType` 方法示範如何使用 <xref:System.Type.IsGenericType%2A>、<xref:System.Type.IsGenericParameter%2A> 和 <xref:System.Type.GenericParameterPosition%2A> 屬性以及 <xref:System.Type.GetGenericArguments%2A> 方法。  
  
 此範例也會定義 `DisplayGenericParameter` 方法，檢查泛型型別參數，並顯示其條件約束。  
  
 程式碼範例會定義一組測試類型，包括說明型別參數條件約束的泛型型別，以及示範如何顯示這些類型的相關資訊。  
  
 此範例會建立型別引數陣列並呼叫 <xref:System.Type.MakeGenericType%2A> 方法，從 <xref:System.Collections.Generic.Dictionary%602> 類別建構類型。 程式會比較使用 <xref:System.Type.MakeGenericType%2A> 建構的 <xref:System.Type> 物件和使用 `typeof` (Visual Basic 為 `GetType`) 取得的 <xref:System.Type> 物件，示範它們是一樣的。 同樣地，程式會使用 <xref:System.Type.GetGenericTypeDefinition%2A> 方法取得建構類型的泛型型別定義，和代表 <xref:System.Collections.Generic.Dictionary%602> 類別的 <xref:System.Type> 物件相比較。  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)] [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)] [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   此程式碼包含編譯所需的 C# `using` 陳述式 (Visual Basic 為 `Imports`)。  
  
-   不需要任何其他組件參考。  
  
-   在命令列使用 csc.exe、vbc.exe 或 cl.exe 編譯程式碼。 若要編譯 Visual Studio 中的程式碼，請將它放在主控台應用程式專案範本。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Type>   
 <xref:System.Reflection.MethodInfo>   
 [反映和泛型型別](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)   
 [檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)   
 [泛型](../../../docs/standard/generics/index.md)

