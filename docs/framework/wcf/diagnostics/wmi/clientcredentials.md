---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c3adc675bb6c1e9011459a88fd7dc8e8cf63a880
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963967"
---
# <a name="clientcredentials"></a><span data-ttu-id="63874-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="63874-102">ClientCredentials</span></span>
<span data-ttu-id="63874-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="63874-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63874-104">語法</span><span class="sxs-lookup"><span data-stu-id="63874-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="63874-105">方法</span><span class="sxs-lookup"><span data-stu-id="63874-105">Methods</span></span>  
 <span data-ttu-id="63874-106">ClientCredentials 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="63874-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="63874-107">屬性</span><span class="sxs-lookup"><span data-stu-id="63874-107">Properties</span></span>  
 <span data-ttu-id="63874-108">ClientCredentials 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="63874-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="63874-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="63874-109">ClientCertificate</span></span>  
 <span data-ttu-id="63874-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63874-110">Data type: string</span></span>  
  
 <span data-ttu-id="63874-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63874-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63874-112">用戶端用來向服務驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="63874-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="63874-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="63874-113">HttpDigest</span></span>  
 <span data-ttu-id="63874-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63874-114">Data type: string</span></span>  
  
 <span data-ttu-id="63874-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63874-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63874-116">目前的 Http 摘要式認證。</span><span class="sxs-lookup"><span data-stu-id="63874-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="63874-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="63874-117">IssuedToken</span></span>  
 <span data-ttu-id="63874-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63874-118">Data type: string</span></span>  
  
 <span data-ttu-id="63874-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63874-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63874-120">用來聯繫本機安全性權杖服務的端點位址與繫結。</span><span class="sxs-lookup"><span data-stu-id="63874-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="63874-121">對等</span><span class="sxs-lookup"><span data-stu-id="63874-121">Peer</span></span>  
 <span data-ttu-id="63874-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63874-122">Data type: string</span></span>  
  
 <span data-ttu-id="63874-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63874-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63874-124">對等節點用來向 mesh 中的其他節點驗證自己時使用的認證。</span><span class="sxs-lookup"><span data-stu-id="63874-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="63874-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="63874-125">ServiceCertificate</span></span>  
 <span data-ttu-id="63874-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63874-126">Data type: string</span></span>  
  
 <span data-ttu-id="63874-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63874-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63874-128">服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="63874-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="63874-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="63874-129">SupportInteractive</span></span>  
 <span data-ttu-id="63874-130">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="63874-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="63874-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63874-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63874-132">指定認證是否支援互動式交涉的布林值。</span><span class="sxs-lookup"><span data-stu-id="63874-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="63874-133">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="63874-133">UserName</span></span>  
 <span data-ttu-id="63874-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63874-134">Data type: string</span></span>  
  
 <span data-ttu-id="63874-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63874-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63874-136">用戶端用來向服務驗證自身的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="63874-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="63874-137">Windows</span><span class="sxs-lookup"><span data-stu-id="63874-137">Windows</span></span>  
 <span data-ttu-id="63874-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63874-138">Data type: string</span></span>  
  
 <span data-ttu-id="63874-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63874-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63874-140">用戶端用來向服務驗證自身的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="63874-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63874-141">需求</span><span class="sxs-lookup"><span data-stu-id="63874-141">Requirements</span></span>  
  
|<span data-ttu-id="63874-142">MOF</span><span class="sxs-lookup"><span data-stu-id="63874-142">MOF</span></span>|<span data-ttu-id="63874-143">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="63874-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="63874-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="63874-144">Namespace</span></span>|<span data-ttu-id="63874-145">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="63874-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63874-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63874-146">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
