---
title: CLR 預存程序
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 736020695ae40a8884057ddee8aac8abe6e8c1fd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554191"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="fa2f0-102">CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="fa2f0-102">CLR Stored Procedures</span></span>
<span data-ttu-id="fa2f0-103">預存程序是無法在純量運算式中使用的常式。</span><span class="sxs-lookup"><span data-stu-id="fa2f0-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="fa2f0-104">它們可將表格式結果及訊息傳回到用戶端、叫用資料定義語言 (DDL) 及資料操作語言 (DML) 陳述式，並傳回輸出參數。</span><span class="sxs-lookup"><span data-stu-id="fa2f0-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa2f0-105">Microsoft Visual Basic 支援輸出參數的方式，與 Microsoft Visual C# 所使用的方式不同。</span><span class="sxs-lookup"><span data-stu-id="fa2f0-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="fa2f0-106">您必須指定以傳址方式傳遞參數，並套用 \<Out()> 屬性以表示輸出參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="fa2f0-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="fa2f0-107">如需詳細資訊，請參閱您所使用之 SQL Server 版本的 [SQL Server 檔](/sql) 版本。</span><span class="sxs-lookup"><span data-stu-id="fa2f0-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="fa2f0-108">**SQL Server 文件**</span><span class="sxs-lookup"><span data-stu-id="fa2f0-108">**SQL Server documentation**</span></span>

1. <span data-ttu-id="fa2f0-109">[CLR 預存程序](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="fa2f0-109">[CLR Stored Procedures](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa2f0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa2f0-110">See also</span></span>

- <span data-ttu-id="fa2f0-111">[在 Managed 程式碼中建立 SQL Server 2005 物件](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fa2f0-111">[Creating SQL Server 2005 Objects In Managed Code](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- <span data-ttu-id="fa2f0-112">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="fa2f0-112">[ADO.NET Overview](../ado-net-overview.md)</span></span>
