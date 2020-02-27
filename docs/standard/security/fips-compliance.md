---
title: FIPS 合規性-.NET Core
description: 說明 .NET Core 聯邦資訊處理標準（FIPS）合規性。
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: 84d6edc6975af0484bb67999ad5891eaf4db057d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626954"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a><span data-ttu-id="c40d2-103">.NET Core 聯邦資訊處理標準（FIPS）合規性</span><span class="sxs-lookup"><span data-stu-id="c40d2-103">.NET Core Federal Information Processing Standard (FIPS) compliance</span></span>

<span data-ttu-id="c40d2-104">聯邦資訊處理標準（FIPS）發行集140-2 是美國政府標準，定義資訊技術產品中密碼編譯模組的最低安全性需求，如資訊第5131節所定義.1996的技術管理改革動作。</span><span class="sxs-lookup"><span data-stu-id="c40d2-104">The Federal Information Processing Standard (FIPS) Publication 140-2 is a U.S. government standard that defines minimum security requirements for cryptographic modules in information technology products, as defined in Section 5131 of the Information Technology Management Reform Act of 1996.</span></span>

<span data-ttu-id="c40d2-105">.NET Core：</span><span class="sxs-lookup"><span data-stu-id="c40d2-105">.NET Core:</span></span>

* <span data-ttu-id="c40d2-106">會將密碼編譯基本呼叫傳遞至基礎作業系統所提供的標準模組。</span><span class="sxs-lookup"><span data-stu-id="c40d2-106">Passes cryptographic primitives calls through to the standard modules the underlying operating system provides.</span></span>
* <span data-ttu-id="c40d2-107">不**會強制在**.net Core 應用程式中使用 FIPS 已核准的演算法或金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="c40d2-107">Does **not** enforce the use of FIPS Approved algorithms or key sizes in .NET Core apps.</span></span>

<span data-ttu-id="c40d2-108">系統管理員負責設定作業系統的 FIPS 合規性。</span><span class="sxs-lookup"><span data-stu-id="c40d2-108">The system administrator is responsible for configuring the FIPS compliance for an operating system.</span></span>

<span data-ttu-id="c40d2-109">如果程式碼是針對符合 FIPS 規範的環境所撰寫，則開發人員會負責確保不會使用不相容的 FIPS 演算法。</span><span class="sxs-lookup"><span data-stu-id="c40d2-109">If code is written for a FIPS-compliant environment, the developer is responsible for ensuring that non-compliant FIPS algorithms aren't used.</span></span>

<span data-ttu-id="c40d2-110">如需 FIPS 合規性的詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="c40d2-110">For more information on FIPS compliance, see the following articles:</span></span>

* [<span data-ttu-id="c40d2-111">Windows FIPS 合規性</span><span class="sxs-lookup"><span data-stu-id="c40d2-111">Windows FIPS Compliance</span></span>](/windows/security/threat-protection/fips-140-validation)
* [<span data-ttu-id="c40d2-112">設定 Windows 以符合 FIPS 規範</span><span class="sxs-lookup"><span data-stu-id="c40d2-112">Configuring Windows for FIPS Compliance</span></span>](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [<span data-ttu-id="c40d2-113">第8章。美國聯邦標準和法規 Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="c40d2-113">Chapter 8. Federal Standards and Regulations Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/chap-federal_standards_and_regulations)
