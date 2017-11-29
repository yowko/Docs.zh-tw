---
title: "如何：使用 WebRequest 註冊自訂通訊協定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4fdb1188aeb7fd754ab21a268070830f55347441
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="10019-102">如何：使用 WebRequest 註冊自訂通訊協定</span><span class="sxs-lookup"><span data-stu-id="10019-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="10019-103">這個範例示範如何註冊在其他位置定義的通訊協定特定類別。</span><span class="sxs-lookup"><span data-stu-id="10019-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="10019-104">在此範例中，`CustomWebRequestCreator` 是使用者實作的物件，其可實作 `CustomWebRequest` 物件傳回的 **Create**方法。</span><span class="sxs-lookup"><span data-stu-id="10019-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="10019-105">此程式碼範例假設您已撰寫實作自訂通訊協定的 `CustomWebRequest` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="10019-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10019-106">範例</span><span class="sxs-lookup"><span data-stu-id="10019-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10019-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="10019-107">Compiling the Code</span></span>  
 <span data-ttu-id="10019-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="10019-108">This example requires:</span></span>  
  
 <span data-ttu-id="10019-109">對 <xref:System.Net> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="10019-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10019-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10019-110">See Also</span></span>  
 [<span data-ttu-id="10019-111">可插式通訊協定程式設計</span><span class="sxs-lookup"><span data-stu-id="10019-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
