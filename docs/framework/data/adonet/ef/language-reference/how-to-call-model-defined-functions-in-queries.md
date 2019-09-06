---
title: 作法：在查詢中呼叫模型定義函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 33f26896dd0d4ff08beb4a011fa6bd468cba7207
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250761"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>HOW TO：在查詢中呼叫模型定義函式
本主題描述如何從 LINQ to Entities 查詢內呼叫概念模型中定義的函數。  
  
 下列程式提供從 LINQ to Entities 查詢中呼叫模型定義函數的高階大綱。 程序後的範例提供程序中之步驟相關詳細資訊。 程序假設您已在概念模型中定義函式。 如需詳細資訊，請參閱[如何：在概念模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))中定義自訂函式。  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>呼叫概念模型中定義的函式  
  
1. 將 Common Language Runtime (CLR) 方法加入至您的應用程式，該方法會對應至概念模型中所定義之函式。 若要對應方法，您必須將 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 套用至方法。 請注意，屬性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 參數分別是概念模型的命名空間名稱和概念模型中的函式名稱。 LINQ 的函式名稱解析是區分大小寫的。  
  
2. 呼叫 LINQ to Entities 查詢中的函式。  
  
## <a name="example"></a>範例  
 下列範例示範如何從 LINQ to Entities 查詢內呼叫概念模型中定義的函數。 範例使用 School 模型。 如需 School 模型的相關資訊，請參閱[建立 School 範例資料庫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))和[產生 school .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))檔案。  
  
 下列概念模型函式會傳回講師受雇之後經過的年份。 如需將函式新增至概念模型的詳細資訊[，請參閱如何：在概念模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))中定義自訂函式）。  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>範例  
 接下來，將下列方法加入至您的應用程式並使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 將它對應至概念模型函式：  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>範例  
 現在您可以從 LINQ to Entities 查詢內呼叫概念模型函數。 下列程式碼會呼叫該方法，顯示受雇超過十年的所有講師：  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [.edmx 檔案總覽](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities 中的查詢](queries-in-linq-to-entities.md)
- [在 LINQ to Entities 查詢中呼叫函式](calling-functions-in-linq-to-entities-queries.md)
- [如何：以物件方法的形式呼叫模型定義函式](how-to-call-model-defined-functions-as-object-methods.md)
