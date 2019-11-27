---
title: FIPS 合規性-.NET Core
description: 說明 .NET Core 聯邦資訊處理標準（FIPS）合規性。
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: cf640c857e79ae811dd38d57a0e5301b7bc96572
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205063"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a><span data-ttu-id="05233-103">.NET Core 聯邦資訊處理標準（FIPS）合規性</span><span class="sxs-lookup"><span data-stu-id="05233-103">.NET Core Federal Information Processing Standard (FIPS) compliance</span></span>

<span data-ttu-id="05233-104">聯邦資訊處理標準（FIPS）發行集140-2 是美國政府標準，定義資訊技術產品中密碼編譯模組的最低安全性需求，如資訊第5131節所定義。1996的技術管理改革動作。</span><span class="sxs-lookup"><span data-stu-id="05233-104">The Federal Information Processing Standard (FIPS) Publication 140-2 is a U.S. government standard that defines minimum security requirements for cryptographic modules in information technology products, as defined in Section 5131 of the Information Technology Management Reform Act of 1996.</span></span>

<span data-ttu-id="05233-105">.NET Core：</span><span class="sxs-lookup"><span data-stu-id="05233-105">.NET Core:</span></span>

* <span data-ttu-id="05233-106">會將密碼編譯基本呼叫傳遞至基礎作業系統所提供的標準模組。</span><span class="sxs-lookup"><span data-stu-id="05233-106">Passes cryptographic primitives calls through to the standard modules the underlying operating system provides.</span></span>
* <span data-ttu-id="05233-107">不**會強制在**.net Core 應用程式中使用 FIPS 已核准的演算法或金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="05233-107">Does **not** enforce the use of FIPS Approved algorithms or key sizes in .NET Core apps.</span></span>

<span data-ttu-id="05233-108">系統管理員負責設定作業系統的 FIPS 合規性。</span><span class="sxs-lookup"><span data-stu-id="05233-108">The system administrator is responsible for configuring the FIPS compliance for an operating system.</span></span>

<span data-ttu-id="05233-109">如果程式碼是針對符合 FIPS 規範的環境所撰寫，則開發人員會負責確保不會使用不相容的 FIPS 演算法。</span><span class="sxs-lookup"><span data-stu-id="05233-109">If code is written for a FIPS-compliant environment, the developer is responsible for ensuring that non-compliant FIPS algorithms aren't used.</span></span>

<span data-ttu-id="05233-110">如需 FIPS 合規性的詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="05233-110">For more information on FIPS compliance, see the following articles:</span></span>

* [<span data-ttu-id="05233-111">Windows FIPS 合規性</span><span class="sxs-lookup"><span data-stu-id="05233-111">Windows FIPS Compliance</span></span>](/windows/security/threat-protection/fips-140-validation)
* [<span data-ttu-id="05233-112">設定 Windows 以符合 FIPS 規範</span><span class="sxs-lookup"><span data-stu-id="05233-112">Configuring Windows for FIPS Compliance</span></span>](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [<span data-ttu-id="05233-113">10.2. 聯邦資訊處理標準（FIPS）</span><span class="sxs-lookup"><span data-stu-id="05233-113">10.2. FEDERAL INFORMATION PROCESSING STANDARD (FIPS)</span></span>](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
