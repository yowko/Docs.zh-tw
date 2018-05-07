---
title: 以獨佔模式使用預存程序來自訂作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 3c60a9e430b4228117fd03a43a30f27342154b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a>以獨佔模式使用預存程序來自訂作業
在常見的案例中使用預存程序存取資料。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 您可以修改提供的範例[自訂作業所使用預存程序](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)即使第一個查詢 （這會導致執行動態 SQL） 取代為方法呼叫包裝預存程序。  
  
 假設 `CustomersByCity` 為下列範例中的方法。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 下列程式碼會在沒有任何動態 SQL 的情況下執行。  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>另請參閱  
 [開發人員覆寫預設行為的責任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
