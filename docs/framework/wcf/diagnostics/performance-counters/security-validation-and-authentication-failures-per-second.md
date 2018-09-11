---
title: 每秒的安全性驗證和驗證失敗數
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4836a5076401de2f7c3112b298cdadc0e0307962
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44261833"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="b517b-102">每秒的安全性驗證和驗證失敗數</span><span class="sxs-lookup"><span data-stu-id="b517b-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="b517b-103">計數器名稱：每秒的安全性驗證和驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="b517b-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b517b-104">描述</span><span class="sxs-lookup"><span data-stu-id="b517b-104">Description</span></span>  
 <span data-ttu-id="b517b-105">每當因為「未授權的安全性呼叫數」計數器所未涵蓋的安全性問題而拒絕訊息時，這個計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="b517b-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="b517b-106">這類問題包括：</span><span class="sxs-lookup"><span data-stu-id="b517b-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="b517b-107">無法從訊息中讀取用戶端權杖。</span><span class="sxs-lookup"><span data-stu-id="b517b-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="b517b-108">用戶端權杖已經驗證失敗 (例如密碼錯誤)。</span><span class="sxs-lookup"><span data-stu-id="b517b-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="b517b-109">簽章驗證已經失敗 (例如訊息遭到竄改)。</span><span class="sxs-lookup"><span data-stu-id="b517b-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="b517b-110">此訊息與之前的訊息重複，這可能會在重新執行攻擊時發生。</span><span class="sxs-lookup"><span data-stu-id="b517b-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="b517b-111">發生解密失敗。</span><span class="sxs-lookup"><span data-stu-id="b517b-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="b517b-112">訊息中遺失某些必要的項目 (例如遺失時間戳記或加密的資料區塊)。</span><span class="sxs-lookup"><span data-stu-id="b517b-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="b517b-113">在 TLSNEGO/SPNEGO 交換期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b517b-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="b517b-114">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，其值會計算公式如下：</span><span class="sxs-lookup"><span data-stu-id="b517b-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="b517b-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="b517b-115">(N1-N0)/((D1-D0)/F)</span></span>
