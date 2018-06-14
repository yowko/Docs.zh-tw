---
title: 使用預存程序來自訂作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: 1220ea07501e68fd8d2a8075c686d949be9a7020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360205"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>使用預存程序來自訂作業
預存程序表示用以覆寫預設行為的常見方法。 本主題中的範例顯示如何使用針對預存程序產生的方法包裝函式，以及如何才能直接呼叫預存程序。  
  
 如果您使用 Visual Studio，您可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]指派來執行插入、 更新和刪除的預存程序。  
  
> [!NOTE]
>  若要讀回資料庫產生的值，請在預存程序中使用輸出參數。 如果您無法使用輸出參數，請撰寫部分方法實作，而不要依賴[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]產生的覆寫作業。 在順利完成 `INSERT` 或 `UPDATE` 作業之後，對應至資料庫產生值的成員必須設為適當的值。 如需詳細資訊，請參閱[開發人員覆寫預設行為的責任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 在下列範例中，假設 `Northwind` 類別有兩種方法可以呼叫用於在衍生類別 (Derived Class) 中覆寫的預存程序。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列類別使用這些方法進行覆寫。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 您使用 `NorthwindThroughSprocs` 的方式完全與使用 `Northwnd` 相同。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱  
 [開發人員覆寫預設行為的責任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
