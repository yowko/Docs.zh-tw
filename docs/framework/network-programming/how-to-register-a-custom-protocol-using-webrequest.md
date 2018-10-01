---
title: 如何：使用 WebRequest 註冊自訂通訊協定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1f78f98f94daa51c17a1294285e13dfddd457106
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47230965"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="e0157-102">如何：使用 WebRequest 註冊自訂通訊協定</span><span class="sxs-lookup"><span data-stu-id="e0157-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="e0157-103">這個範例示範如何註冊在其他位置定義的通訊協定特定類別。</span><span class="sxs-lookup"><span data-stu-id="e0157-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="e0157-104">在此範例中，`CustomWebRequestCreator` 是使用者實作的物件，其可實作 `CustomWebRequest` 物件傳回的 **Create**方法。</span><span class="sxs-lookup"><span data-stu-id="e0157-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="e0157-105">此程式碼範例假設您已撰寫實作自訂通訊協定的 `CustomWebRequest` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e0157-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0157-106">範例</span><span class="sxs-lookup"><span data-stu-id="e0157-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0157-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e0157-107">Compiling the Code</span></span>  
 <span data-ttu-id="e0157-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e0157-108">This example requires:</span></span>  
  
 <span data-ttu-id="e0157-109">對 <xref:System.Net> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="e0157-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0157-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0157-110">See Also</span></span>  
 [<span data-ttu-id="e0157-111">可插式通訊協定程式設計</span><span class="sxs-lookup"><span data-stu-id="e0157-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
