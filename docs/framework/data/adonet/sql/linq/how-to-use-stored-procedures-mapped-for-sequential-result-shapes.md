---
title: "如何：使用與循序結果型式對應的預存程序"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a110cf2f321915ef65c571a30a19c5a29bdb8af2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>如何：使用與循序結果型式對應的預存程序
這種預存程序可以產生一個以上的結果圖案，但您會知道傳回結果的順序。 將此案例與您不知道傳回順序的案例相比較。 如需詳細資訊，請參閱[How to： 使用預存程序對應要進行多個結果圖案](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)。  
  
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
 [預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
