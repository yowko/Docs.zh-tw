---
title: 安全性驗證和驗證失敗數
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 32a7d41f93dd99f1950a073e1cac1b62177ff6c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916041"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="166fc-102">安全性驗證和驗證失敗數</span><span class="sxs-lookup"><span data-stu-id="166fc-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="166fc-103">計數器名稱：安全性驗證和驗證失敗數</span><span class="sxs-lookup"><span data-stu-id="166fc-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="166fc-104">描述</span><span class="sxs-lookup"><span data-stu-id="166fc-104">Description</span></span>  
 <span data-ttu-id="166fc-105">每當因為「未授權的安全性呼叫數」計數器所未涵蓋的安全性問題而拒絕訊息時，這個計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="166fc-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="166fc-106">這類問題包括：</span><span class="sxs-lookup"><span data-stu-id="166fc-106">Such problems include:</span></span>  
  
- <span data-ttu-id="166fc-107">無法從訊息中讀取用戶端權杖。</span><span class="sxs-lookup"><span data-stu-id="166fc-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="166fc-108">用戶端權杖已經驗證失敗 (例如密碼錯誤)。</span><span class="sxs-lookup"><span data-stu-id="166fc-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="166fc-109">簽章驗證已經失敗 (例如訊息遭到竄改)。</span><span class="sxs-lookup"><span data-stu-id="166fc-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="166fc-110">此訊息與之前的訊息重複，這可能會在重新執行攻擊時發生。</span><span class="sxs-lookup"><span data-stu-id="166fc-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="166fc-111">發生解密失敗。</span><span class="sxs-lookup"><span data-stu-id="166fc-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="166fc-112">訊息中遺失某些必要的項目 (例如遺失時間戳記或加密的資料區塊)。</span><span class="sxs-lookup"><span data-stu-id="166fc-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="166fc-113">在 TLSNEGO/SPNEGO 交換期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="166fc-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
