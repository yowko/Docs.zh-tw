---
title: 以獨佔模式使用預存程序來自訂作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 78db5cf448a19056d7265ab84d97d055748c3faa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164320"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a>以獨佔模式使用預存程序來自訂作業

在常見的案例中使用預存程序存取資料。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  

 您可以 [使用預存程式來修改自訂作業](customizing-operations-by-using-stored-procedures.md) 中提供的範例，方法是以包裝預存程式的方法呼叫取代第一個查詢 (，這會導致動態 SQL 執行) 。  
  
 假設 `CustomersByCity` 為下列範例中的方法。  
  
### <a name="code"></a>程式碼  

 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 下列程式碼會在沒有任何動態 SQL 的情況下執行。  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [開發人員覆寫預設行為的責任](responsibilities-of-the-developer-in-overriding-default-behavior.md)
