---
title: HOW TO：使用對應的循序結果型式的預存程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 296870029d2329640466b3a540e9057738173aa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495652"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>HOW TO：使用對應的循序結果型式的預存程序
這種預存程序可以產生一個以上的結果圖案，但您會知道傳回結果的順序。 將此案例與您不知道傳回順序的案例相比較。 如需詳細資訊，請參閱[＜How to：使用對應的多個結果圖案的預存程序](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)。  
  
## <a name="example"></a>範例  
 以下是可循序傳回多個結果圖案之預存程序的 T-SQL：  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>範例  
 您可使用類似下列的程式碼來執行此預存程序。  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>另請參閱
- [預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
