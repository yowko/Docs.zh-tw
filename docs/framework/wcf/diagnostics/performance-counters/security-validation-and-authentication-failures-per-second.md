---
title: 每秒的安全性驗證和驗證失敗數
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 546d81b73e912915d265fb194de4ad9e45d55cea
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163913"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="d76e6-102">每秒的安全性驗證和驗證失敗數</span><span class="sxs-lookup"><span data-stu-id="d76e6-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="d76e6-103">計數器名稱：每秒的安全性驗證和驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="d76e6-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d76e6-104">描述</span><span class="sxs-lookup"><span data-stu-id="d76e6-104">Description</span></span>  
 <span data-ttu-id="d76e6-105">每當因為「未授權的安全性呼叫數」計數器所未涵蓋的安全性問題而拒絕訊息時，這個計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="d76e6-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="d76e6-106">這類問題包括：</span><span class="sxs-lookup"><span data-stu-id="d76e6-106">Such problems include:</span></span>  
  
- <span data-ttu-id="d76e6-107">無法從訊息中讀取用戶端權杖。</span><span class="sxs-lookup"><span data-stu-id="d76e6-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="d76e6-108">用戶端權杖已經驗證失敗 (例如密碼錯誤)。</span><span class="sxs-lookup"><span data-stu-id="d76e6-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="d76e6-109">簽章驗證已經失敗 (例如訊息遭到竄改)。</span><span class="sxs-lookup"><span data-stu-id="d76e6-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="d76e6-110">此訊息與之前的訊息重複，這可能會在重新執行攻擊時發生。</span><span class="sxs-lookup"><span data-stu-id="d76e6-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="d76e6-111">發生解密失敗。</span><span class="sxs-lookup"><span data-stu-id="d76e6-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="d76e6-112">訊息中遺失某些必要的項目 (例如遺失時間戳記或加密的資料區塊)。</span><span class="sxs-lookup"><span data-stu-id="d76e6-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="d76e6-113">在 TLSNEGO/SPNEGO 交換期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="d76e6-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="d76e6-114">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算：</span><span class="sxs-lookup"><span data-stu-id="d76e6-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="d76e6-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="d76e6-115">(N1-N0)/((D1-D0)/F)</span></span>
