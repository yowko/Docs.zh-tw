---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: 8b6200f84f352d49cf142d9c8b97d1c2b36149b2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180896"
---
# <a name="clientcredentials"></a><span data-ttu-id="28566-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="28566-102">ClientCredentials</span></span>
<span data-ttu-id="28566-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="28566-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28566-104">語法</span><span class="sxs-lookup"><span data-stu-id="28566-104">Syntax</span></span>  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="28566-105">方法</span><span class="sxs-lookup"><span data-stu-id="28566-105">Methods</span></span>  
 <span data-ttu-id="28566-106">ClientCredentials 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="28566-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="28566-107">屬性</span><span class="sxs-lookup"><span data-stu-id="28566-107">Properties</span></span>  
 <span data-ttu-id="28566-108">ClientCredentials 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="28566-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="28566-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="28566-109">ClientCertificate</span></span>  
 <span data-ttu-id="28566-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="28566-110">Data type: string</span></span>  
  
 <span data-ttu-id="28566-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="28566-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28566-112">用戶端用來向服務驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="28566-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="28566-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="28566-113">HttpDigest</span></span>  
 <span data-ttu-id="28566-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="28566-114">Data type: string</span></span>  
  
 <span data-ttu-id="28566-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="28566-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28566-116">目前的 Http 摘要式認證。</span><span class="sxs-lookup"><span data-stu-id="28566-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="28566-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="28566-117">IssuedToken</span></span>  
 <span data-ttu-id="28566-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="28566-118">Data type: string</span></span>  
  
 <span data-ttu-id="28566-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="28566-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28566-120">用來聯繫本機安全性權杖服務的端點位址與繫結。</span><span class="sxs-lookup"><span data-stu-id="28566-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="28566-121">對等</span><span class="sxs-lookup"><span data-stu-id="28566-121">Peer</span></span>  
 <span data-ttu-id="28566-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="28566-122">Data type: string</span></span>  
  
 <span data-ttu-id="28566-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="28566-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28566-124">對等節點用來向 mesh 中的其他節點驗證自己時使用的認證。</span><span class="sxs-lookup"><span data-stu-id="28566-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="28566-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="28566-125">ServiceCertificate</span></span>  
 <span data-ttu-id="28566-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="28566-126">Data type: string</span></span>  
  
 <span data-ttu-id="28566-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="28566-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28566-128">服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="28566-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="28566-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="28566-129">SupportInteractive</span></span>  
 <span data-ttu-id="28566-130">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="28566-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="28566-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="28566-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28566-132">指定認證是否支援互動式交涉的布林值。</span><span class="sxs-lookup"><span data-stu-id="28566-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="28566-133">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="28566-133">UserName</span></span>  
 <span data-ttu-id="28566-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="28566-134">Data type: string</span></span>  
  
 <span data-ttu-id="28566-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="28566-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28566-136">用戶端用來向服務驗證自身的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="28566-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="28566-137">Windows</span><span class="sxs-lookup"><span data-stu-id="28566-137">Windows</span></span>  
 <span data-ttu-id="28566-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="28566-138">Data type: string</span></span>  
  
 <span data-ttu-id="28566-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="28566-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28566-140">用戶端用來向服務驗證自身的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="28566-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28566-141">需求</span><span class="sxs-lookup"><span data-stu-id="28566-141">Requirements</span></span>  
  
|<span data-ttu-id="28566-142">MOF</span><span class="sxs-lookup"><span data-stu-id="28566-142">MOF</span></span>|<span data-ttu-id="28566-143">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="28566-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="28566-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="28566-144">Namespace</span></span>|<span data-ttu-id="28566-145">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="28566-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28566-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28566-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
