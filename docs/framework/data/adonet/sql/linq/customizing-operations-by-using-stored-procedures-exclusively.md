---
title: 以獨佔模式使用預存程序來自訂作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 61230ffc5cd055ee64de9d519cdfb4d76c856ca3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038047"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a>以獨佔模式使用預存程序來自訂作業
在常見的案例中使用預存程序存取資料。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 您可以修改中提供的範例[自訂作業藉由使用預存程序](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)藉由包裝預存程序的方法呼叫中取代甚至是第一個查詢 （這會導致動態 SQL 執行）。  
  
 假設 `CustomersByCity` 為下列範例中的方法。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 下列程式碼會在沒有任何動態 SQL 的情況下執行。  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [開發人員覆寫預設行為的責任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
