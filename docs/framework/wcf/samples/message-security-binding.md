---
title: "訊息安全性繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4570ce7-864e-461b-85d8-0f7bcc53c2c8
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f0c8b125d3fc313dca4140b871ccea8165329fda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-binding"></a><span data-ttu-id="eb7f8-102">訊息安全性繫結</span><span class="sxs-lookup"><span data-stu-id="eb7f8-102">Message Security Binding</span></span>
<span data-ttu-id="eb7f8-103">本節包含示範 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中 Windows 服務之訊息安全性繫結的範例。</span><span class="sxs-lookup"><span data-stu-id="eb7f8-103">This section contains samples that demonstrate message security binding in Windows Services in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb7f8-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="eb7f8-104">In This Section</span></span>  
 [<span data-ttu-id="eb7f8-105">訊息安全性匿名</span><span class="sxs-lookup"><span data-stu-id="eb7f8-105">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 <span data-ttu-id="eb7f8-106">這個範例會示範如何實作 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式，這個應用程式所使用的訊息層級安全性並不會透過用戶端驗證，而是要求以伺服器的 X.509 憑證進行伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="eb7f8-106">This sample demonstrates how to implement a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span>  
  
 [<span data-ttu-id="eb7f8-107">訊息安全性憑證</span><span class="sxs-lookup"><span data-stu-id="eb7f8-107">Message Security Certificate</span></span>](../../../../docs/framework/wcf/samples/message-security-certificate.md)  
 <span data-ttu-id="eb7f8-108">這個範例會示範如何實作應用程式，該應用程式會對用戶端使用搭配 X.509 v3 憑證驗證的 WS-Security，並要求使用伺服器之 X.509 v3 憑證進行驗證的伺服器。</span><span class="sxs-lookup"><span data-stu-id="eb7f8-108">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span>  
  
 [<span data-ttu-id="eb7f8-109">訊息安全性使用者名稱</span><span class="sxs-lookup"><span data-stu-id="eb7f8-109">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 <span data-ttu-id="eb7f8-110">這個範例會示範如何實作應用程式，該應用程式會對用戶端使用搭配使用者名稱驗證的 WS-Security，並要求使用伺服器之 X.509v3 憑證進行驗證的伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="eb7f8-110">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span>  
  
 [<span data-ttu-id="eb7f8-111">訊息安全性視窗</span><span class="sxs-lookup"><span data-stu-id="eb7f8-111">Message Security Windows</span></span>](../../../../docs/framework/wcf/samples/message-security-windows.md)  
 <span data-ttu-id="eb7f8-112">這個範例會示範如何將 <xref:System.ServiceModel.WSHttpBinding> 繫結設定成搭配 Windows 驗證使用的訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="eb7f8-112">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span>
