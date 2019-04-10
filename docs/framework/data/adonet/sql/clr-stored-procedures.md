---
title: CLR 預存程序
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 9b31d93c1ebc0af9aa8e41b3a4c328af62da7e23
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230807"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="33b9c-102">CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="33b9c-102">CLR Stored Procedures</span></span>
<span data-ttu-id="33b9c-103">預存程序是無法在純量運算式中使用的常式。</span><span class="sxs-lookup"><span data-stu-id="33b9c-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="33b9c-104">它們可將表格式結果及訊息傳回到用戶端、叫用資料定義語言 (DDL) 及資料操作語言 (DML) 陳述式，並傳回輸出參數。</span><span class="sxs-lookup"><span data-stu-id="33b9c-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33b9c-105">Microsoft Visual Basic 支援輸出參數的方式，與 Microsoft Visual C# 所使用的方式不同。</span><span class="sxs-lookup"><span data-stu-id="33b9c-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="33b9c-106">您必須指定以傳址方式傳遞參數，並套用\<Out() > 屬性以表示 output 參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="33b9c-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="33b9c-107">如需詳細資訊，請參閱的新版[SQL Server 文件](/sql)您使用的 SQL Server 的版本。</span><span class="sxs-lookup"><span data-stu-id="33b9c-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 **<span data-ttu-id="33b9c-108">SQL Server 文件</span><span class="sxs-lookup"><span data-stu-id="33b9c-108">SQL Server documentation</span></span>**

1. [<span data-ttu-id="33b9c-109">CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="33b9c-109">CLR Stored Procedures</span></span>](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="33b9c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33b9c-110">See also</span></span>

- [<span data-ttu-id="33b9c-111">在 Managed 程式碼中建立 SQL Server 2005 物件</span><span class="sxs-lookup"><span data-stu-id="33b9c-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [<span data-ttu-id="33b9c-112">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="33b9c-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
