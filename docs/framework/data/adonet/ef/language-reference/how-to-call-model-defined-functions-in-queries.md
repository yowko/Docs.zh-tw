---
title: HOW TO：在查詢中呼叫模型定義函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 2fe0360a0548bddb0ebba566eca0d121c9ec9160
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300615"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>HOW TO：在查詢中呼叫模型定義函式
本主題描述如何從 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢內呼叫概念模型中所定義的函式。  
  
 以下程序提供從 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢內呼叫模型定義函式的高階概述。 程序後的範例提供程序中之步驟相關詳細資訊。 程序假設您已在概念模型中定義函式。 如需詳細資訊，請參閱[如何：概念模型中定義自訂函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))。  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>呼叫概念模型中定義的函式  
  
1. 將 Common Language Runtime (CLR) 方法加入至您的應用程式，該方法會對應至概念模型中所定義之函式。 若要對應方法，您必須將 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 套用至方法。 請注意，屬性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 參數分別是概念模型的命名空間名稱和概念模型中的函式名稱。 LINQ 的函式名稱解析是區分大小寫的。  
  
2. 在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢中呼叫函式。  
  
## <a name="example"></a>範例  
 下列範例示範如何從 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢內呼叫概念模型中所定義的函式。 範例使用 School 模型。 如需 School 模型的詳細資訊，請參閱[建立 School 範例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))並[產生 School.edmx 檔案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))。  
  
 下列概念模型函式會傳回講師受雇之後經過的年份。 如需加入函式至概念模型資訊，請參閱[How to:概念模型中定義自訂函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))。)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>範例  
 接下來，將下列方法加入至您的應用程式並使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 將它對應至概念模型函式：  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>範例  
 現在，您可以從 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢內呼叫概念模型函式。 下列程式碼會呼叫該方法，顯示受雇超過十年的所有講師：  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [.edmx 檔案概觀](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [在 LINQ to Entities 查詢中呼叫函式](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [如何：呼叫模型定義函式當做物件方法](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
