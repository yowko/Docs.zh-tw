---
title: HOW TO：使用純量值使用者定義函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: ffb24468c81cb4ec9f41645f8888c2c4ba021609
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033575"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>HOW TO：使用純量值使用者定義函式
您可以使用 <xref:System.Data.Linq.Mapping.FunctionAttribute> 屬性，將定義於類別的用戶端方法對應至使用者定義的函式。 請注意，方法的主體會建構一個可擷取方法呼叫用途的運算式，並將該運算式傳遞至 <xref:System.Data.Linq.DataContext> 進行轉譯和執行。  
  
> [!NOTE]
>  唯有在查詢之外呼叫函式時，才會發生直接執行。 如需詳細資訊，請參閱[如何：呼叫使用者定義函式內嵌](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)。  
  
## <a name="example"></a>範例  
 下列 SQL 程式碼展示使用者定義的純量值函式 `ReverseCustName()`。  
  
```  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 您可以對此程式碼對應如下所列的用戶端方法：  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [使用者定義函式](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
