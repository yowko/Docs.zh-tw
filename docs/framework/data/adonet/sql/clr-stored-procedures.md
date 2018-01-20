---
title: "CLR 預存程序"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2259574ef96c17dae4c24be549e28dcb03aaa283
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="974e7-102">CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="974e7-102">CLR Stored Procedures</span></span>
<span data-ttu-id="974e7-103">預存程序是無法在純量運算式中使用的常式。</span><span class="sxs-lookup"><span data-stu-id="974e7-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="974e7-104">它們可將表格式結果及訊息傳回到用戶端、叫用資料定義語言 (DDL) 及資料操作語言 (DML) 陳述式，並傳回輸出參數。</span><span class="sxs-lookup"><span data-stu-id="974e7-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="974e7-105">Microsoft Visual Basic 支援輸出參數的方式，與 Microsoft Visual C# 所使用的方式不同。</span><span class="sxs-lookup"><span data-stu-id="974e7-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="974e7-106">您必須指定傳址方式傳遞參數，並套用\<Out() > 屬性以表示 output 參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="974e7-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 <span data-ttu-id="974e7-107">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="974e7-107">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="974e7-108">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="974e7-108">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="974e7-109">CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="974e7-109">CLR Stored Procedures</span></span>](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="974e7-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="974e7-110">See Also</span></span>  
 [<span data-ttu-id="974e7-111">在 Managed 程式碼中建立 SQL Server 2005 物件</span><span class="sxs-lookup"><span data-stu-id="974e7-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="974e7-112">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="974e7-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
