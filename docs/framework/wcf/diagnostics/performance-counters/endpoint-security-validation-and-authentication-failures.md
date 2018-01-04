---
title: "端點：安全性驗證和驗證失敗數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5bd38ae0e3506397378b7c59976c6c692045054d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="c8a06-102">端點：安全性驗證和驗證失敗數</span><span class="sxs-lookup"><span data-stu-id="c8a06-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="c8a06-103">計數器名稱：安全性驗證和驗證失敗數</span><span class="sxs-lookup"><span data-stu-id="c8a06-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8a06-104">描述</span><span class="sxs-lookup"><span data-stu-id="c8a06-104">Description</span></span>  
 <span data-ttu-id="c8a06-105">每當因為「未授權的安全性呼叫數」計數器所未涵蓋的安全性問題而拒絕訊息時，這個計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="c8a06-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="c8a06-106">這類問題包括：</span><span class="sxs-lookup"><span data-stu-id="c8a06-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="c8a06-107">無法從訊息中讀取用戶端權杖。</span><span class="sxs-lookup"><span data-stu-id="c8a06-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="c8a06-108">用戶端權杖已經驗證失敗 (密碼錯誤)。</span><span class="sxs-lookup"><span data-stu-id="c8a06-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="c8a06-109">簽章驗證已經失敗 (訊息遭到竄改)。</span><span class="sxs-lookup"><span data-stu-id="c8a06-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="c8a06-110">此訊息與之前的訊息重複，這可能會在重新執行攻擊時發生。</span><span class="sxs-lookup"><span data-stu-id="c8a06-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="c8a06-111">發生解密失敗。</span><span class="sxs-lookup"><span data-stu-id="c8a06-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="c8a06-112">訊息中遺失某些必要的元素 (遺失時間戳記或加密的資料區塊)。</span><span class="sxs-lookup"><span data-stu-id="c8a06-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="c8a06-113">在 TLSNEGO/SPNEGO 交換期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8a06-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
