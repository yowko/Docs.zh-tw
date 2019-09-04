---
title: 以獨佔模式使用預存程序來自訂作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: a242ecdc774d67721aee640e75847317c1b815d6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247552"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a>以獨佔模式使用預存程序來自訂作業
在常見的案例中使用預存程序存取資料。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 您可以[使用預存程式來修改自訂作業](customizing-operations-by-using-stored-procedures.md)中提供的範例, 方法是將第一個查詢 (也就是造成動態 SQL 執行) 取代為包裝預存程式的方法呼叫。  
  
 假設 `CustomersByCity` 為下列範例中的方法。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 下列程式碼會在沒有任何動態 SQL 的情況下執行。  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [開發人員覆寫預設行為的責任](responsibilities-of-the-developer-in-overriding-default-behavior.md)
