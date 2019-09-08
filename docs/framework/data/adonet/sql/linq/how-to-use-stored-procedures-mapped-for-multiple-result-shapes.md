---
title: 作法：使用與多個結果型式對應的預存程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: d32faf026789923ca4343271c9fd1b6bbdb068df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793101"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>HOW TO：使用與多個結果型式對應的預存程序
如果預存程序 (Stored Procedure) 可以傳回多個結果圖案，則傳回型別不可以強型別 (Strongly Typed) 為單一投影圖案。 雖然[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]可以產生所有可能的投射類型，但它無法得知傳回的順序。  
  
 請將這個案例與循序產生多個結果圖案的預存程序案例比較。 如需詳細資訊，請參閱[如何：針對順序結果圖形](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)使用對應的預存程式。  
  
 <xref:System.Data.Linq.Mapping.ResultTypeAttribute> 屬性 (Attribute) 會套用至傳回多個結果型別的預存程序，以指定程序可以傳回的型別集。  
  
## <a name="example"></a>範例  
 在下列 SQL 程式碼範例中，結果圖案會根據輸入 (`shape =1` 或 `shape = 2`) 而不同。 您無法得知會先傳回哪個投影。  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>範例  
 您可使用類似下列的程式碼來執行此預存程序。  
  
> [!NOTE]
> 您必須使用 <xref:System.Data.Linq.IMultipleResults.GetResult%2A> 模式，根據您對預存程序的了解以取得正確型別的列舉值。  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [預存程序](stored-procedures.md)
