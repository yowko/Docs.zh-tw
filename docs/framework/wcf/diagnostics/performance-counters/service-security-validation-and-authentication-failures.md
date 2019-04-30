---
title: 服務：安全性驗證和驗證失敗數
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: ba8da3ae6be6bd089690359f19e153da1e0b54fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998305"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="c5e52-102">服務：安全性驗證和驗證失敗數</span><span class="sxs-lookup"><span data-stu-id="c5e52-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="c5e52-103">計數器名稱：安全性驗證和驗證失敗數</span><span class="sxs-lookup"><span data-stu-id="c5e52-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="c5e52-104">描述</span><span class="sxs-lookup"><span data-stu-id="c5e52-104">Description</span></span>  
 <span data-ttu-id="c5e52-105">每當因為「未授權的安全性呼叫數」計數器所未涵蓋的安全性問題而拒絕訊息時，這個計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="c5e52-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="c5e52-106">這類問題包括：</span><span class="sxs-lookup"><span data-stu-id="c5e52-106">Such problems include:</span></span>  
  
- <span data-ttu-id="c5e52-107">無法從訊息中讀取用戶端權杖。</span><span class="sxs-lookup"><span data-stu-id="c5e52-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="c5e52-108">用戶端權杖已經驗證失敗 (例如密碼錯誤)。</span><span class="sxs-lookup"><span data-stu-id="c5e52-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
- <span data-ttu-id="c5e52-109">簽章驗證已經失敗 (例如訊息遭到竄改)。</span><span class="sxs-lookup"><span data-stu-id="c5e52-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
- <span data-ttu-id="c5e52-110">此訊息與之前的訊息重複，這可能會在重新執行攻擊時發生。</span><span class="sxs-lookup"><span data-stu-id="c5e52-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="c5e52-111">發生解密失敗。</span><span class="sxs-lookup"><span data-stu-id="c5e52-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="c5e52-112">訊息中遺漏某些必要的項目 (例如遺漏時間戳記或加密的資料區塊)。</span><span class="sxs-lookup"><span data-stu-id="c5e52-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="c5e52-113">在 TLSNEGO/SPNEGO 交換期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c5e52-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
