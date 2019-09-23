---
title: 安全性
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |安全級
ms.date: 06/30/2019
ms.openlocfilehash: 848255de70038798417a558543d0b1ea8cff1e37
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184768"
---
# <a name="security"></a><span data-ttu-id="382d0-103">安全性</span><span class="sxs-lookup"><span data-stu-id="382d0-103">Security</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="382d0-104">這不是一天的時間，那就是新聞不會包含某個公司遭到駭客入侵或失去客戶資料的部分。</span><span class="sxs-lookup"><span data-stu-id="382d0-104">Not a day goes by where the news doesn't contain some story about a company being hacked or somehow losing their customers' data.</span></span> <span data-ttu-id="382d0-105">即使是國家/地區也不會將安全性視為事後所建立的問題。</span><span class="sxs-lookup"><span data-stu-id="382d0-105">Even countries aren't immune to the problems created by treating security as an afterthought.</span></span> <span data-ttu-id="382d0-106">多年來，公司已經處理客戶資料的安全性，事實上，他們的整個網路都是「不錯」的東西。</span><span class="sxs-lookup"><span data-stu-id="382d0-106">For years, companies have treated the security of customer data and, in fact, their entire networks as something of a "nice to have".</span></span> <span data-ttu-id="382d0-107">Windows 伺服器不會被修補，古版本的 PHP 持續執行，而 MongoDB 資料庫則保持在世界各地開放。</span><span class="sxs-lookup"><span data-stu-id="382d0-107">Windows servers were left unpatched, ancient versions of PHP kept running and MongoDB databases left wide open to the world.</span></span>

<span data-ttu-id="382d0-108">不過，在建立和部署應用程式時，不會有實際的安全性思維方式。</span><span class="sxs-lookup"><span data-stu-id="382d0-108">However, there are starting to be real-world consequences for not maintaining a security mindset when building and deploying applications.</span></span> <span data-ttu-id="382d0-109">許多公司都學到當伺服器和桌上型電腦未在[NotPetya](https://www.wired.com/story/notpetya-cyberattack-ukraine-russia-code-crashed-the-world/)的2017爆發期間進行修補時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="382d0-109">Many companies learned the hard way what can happen when servers and desktops aren't patched during the 2017 outbreak of [NotPetya](https://www.wired.com/story/notpetya-cyberattack-ukraine-russia-code-crashed-the-world/).</span></span> <span data-ttu-id="382d0-110">這些攻擊的成本很容易到達數十億，其中一些估計會將此單一攻擊的損失從10000000000美元起。</span><span class="sxs-lookup"><span data-stu-id="382d0-110">The cost of these attacks has easily reached into the billions, with some estimates putting the losses from this single attack at 10 billion US dollars.</span></span>

<span data-ttu-id="382d0-111">即使是政府也不會受到入侵事件的攻擊。</span><span class="sxs-lookup"><span data-stu-id="382d0-111">Even governments aren't immune to hacking incidents.</span></span> <span data-ttu-id="382d0-112">巴爾的摩的城市被[犯罪](https://www.vox.com/recode/2019/5/21/18634505/baltimore-ransom-robbinhood-mayor-jack-young-hackers)ransom，讓公民無法支付自己的帳單或使用城市服務。</span><span class="sxs-lookup"><span data-stu-id="382d0-112">The city of Baltimore was held ransom by [criminals](https://www.vox.com/recode/2019/5/21/18634505/baltimore-ransom-robbinhood-mayor-jack-young-hackers) making it impossible for citizens to pay their bills or use city services.</span></span>

<span data-ttu-id="382d0-113">法規也會增加，以規定個人資料的特定資料保護。</span><span class="sxs-lookup"><span data-stu-id="382d0-113">There has also been an increase in legislation that mandates certain data protections for personal data.</span></span> <span data-ttu-id="382d0-114">在歐洲，GDPR 已有超過一年的效果，而且最近的加州已將自己的版本稱為 CCDA，這會在2020年1月1日生效。</span><span class="sxs-lookup"><span data-stu-id="382d0-114">In Europe, GDPR has been in effect for more than a year and, more recently, California passed their own version called CCDA, which comes into effect January 1, 2020.</span></span> <span data-ttu-id="382d0-115">GDPR 下的罰款可能會處罰，讓公司不在企業外。</span><span class="sxs-lookup"><span data-stu-id="382d0-115">The fines under GDPR can be so punishing as to put companies out of business.</span></span> <span data-ttu-id="382d0-116">Google 已精細處理50000000歐元進行違規，但這只是與潛在罰款相較之下的一個下降。</span><span class="sxs-lookup"><span data-stu-id="382d0-116">Google has already been fined 50 million Euros for violations, but that's just a drop in the bucket compared with the potential fines.</span></span>

<span data-ttu-id="382d0-117">簡言之，安全性是一項很重要的業務。</span><span class="sxs-lookup"><span data-stu-id="382d0-117">In short, security is serious business.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="382d0-118">[上一頁](identity-server.md)
>[下一頁](azure-security.md)</span><span class="sxs-lookup"><span data-stu-id="382d0-118">[Previous](identity-server.md)
[Next](azure-security.md)</span></span>
