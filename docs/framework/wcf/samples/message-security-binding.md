---
title: 訊息安全性繫結
ms.date: 03/30/2017
ms.assetid: a4570ce7-864e-461b-85d8-0f7bcc53c2c8
ms.openlocfilehash: 7c4b21a8983884cbb4f8ab77568bd4977563b3b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584827"
---
# <a name="message-security-binding"></a><span data-ttu-id="ee449-102">訊息安全性繫結</span><span class="sxs-lookup"><span data-stu-id="ee449-102">Message Security Binding</span></span>
<span data-ttu-id="ee449-103">本節包含的範例會示範 WCF 中 Windows 服務的訊息安全性系結。</span><span class="sxs-lookup"><span data-stu-id="ee449-103">This section contains samples that demonstrate message security binding in Windows Services in WCF.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee449-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="ee449-104">In This Section</span></span>  
 [<span data-ttu-id="ee449-105">訊息安全性匿名</span><span class="sxs-lookup"><span data-stu-id="ee449-105">Message Security Anonymous</span></span>](message-security-anonymous.md)  
 <span data-ttu-id="ee449-106">這個範例示範如何使用不具用戶端驗證的訊息層級安全性來執行 Windows Communication Foundation （WCF）應用程式，但這需要使用伺服器的 x.509 憑證進行伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="ee449-106">This sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span>  
  
 [<span data-ttu-id="ee449-107">訊息安全性憑證</span><span class="sxs-lookup"><span data-stu-id="ee449-107">Message Security Certificate</span></span>](message-security-certificate.md)  
 <span data-ttu-id="ee449-108">這個範例會示範如何實作應用程式，該應用程式會對用戶端使用搭配 X.509 v3 憑證驗證的 WS-Security，並要求使用伺服器之 X.509 v3 憑證進行驗證的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ee449-108">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span>  
  
 [<span data-ttu-id="ee449-109">訊息安全性使用者名稱</span><span class="sxs-lookup"><span data-stu-id="ee449-109">Message Security User Name</span></span>](message-security-user-name.md)  
 <span data-ttu-id="ee449-110">這個範例會示範如何實作應用程式，該應用程式會對用戶端使用搭配使用者名稱驗證的 WS-Security，並要求使用伺服器之 X.509v3 憑證進行驗證的伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="ee449-110">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span>  
  
 [<span data-ttu-id="ee449-111">訊息安全性視窗</span><span class="sxs-lookup"><span data-stu-id="ee449-111">Message Security Windows</span></span>](message-security-windows.md)  
 <span data-ttu-id="ee449-112">這個範例會示範如何將 <xref:System.ServiceModel.WSHttpBinding> 繫結設定成搭配 Windows 驗證使用的訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="ee449-112">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span>
