---
title: 部分信任最佳做法
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: 6c01824ef3d86600fd946e7f510b854b5138ec00
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603875"
---
# <a name="partial-trust-best-practices"></a><span data-ttu-id="9ec78-102">部分信任最佳做法</span><span class="sxs-lookup"><span data-stu-id="9ec78-102">Partial Trust Best Practices</span></span>
<span data-ttu-id="9ec78-103">在部分信任環境中執行 Windows Communication Foundation (WCF) 時，本主題會描述最佳作法。</span><span class="sxs-lookup"><span data-stu-id="9ec78-103">This topic describes best practices when running Windows Communication Foundation (WCF) in a partial trust environment.</span></span>  
  
## <a name="serialization"></a><span data-ttu-id="9ec78-104">序列化</span><span class="sxs-lookup"><span data-stu-id="9ec78-104">Serialization</span></span>  
 <span data-ttu-id="9ec78-105">在部分信任的應用程式中使用 <xref:System.Runtime.Serialization.DataContractSerializer> 時，請套用下列做法。</span><span class="sxs-lookup"><span data-stu-id="9ec78-105">Apply the following practices when using the <xref:System.Runtime.Serialization.DataContractSerializer> in a partially-trusted application.</span></span>  
  
- <span data-ttu-id="9ec78-106">所有可序列化的型別必須明確地加上 `[DataContract]` 屬性標記。</span><span class="sxs-lookup"><span data-stu-id="9ec78-106">All serializable types must be explicitly marked with the `[DataContract]` attribute.</span></span> <span data-ttu-id="9ec78-107">部分信任環境不支援下列技巧：</span><span class="sxs-lookup"><span data-stu-id="9ec78-107">The following techniques are not supported in a partial trust environment:</span></span>  
  
- <span data-ttu-id="9ec78-108">使用 <xref:System.SerializableAttribute> 來標示要序列化的類別。</span><span class="sxs-lookup"><span data-stu-id="9ec78-108">Marking classes to be serialized with the <xref:System.SerializableAttribute>.</span></span>  
  
- <span data-ttu-id="9ec78-109">實作 <xref:System.Runtime.Serialization.ISerializable> 介面以允許類別控制自己的序列化處理序。</span><span class="sxs-lookup"><span data-stu-id="9ec78-109">Implementing the <xref:System.Runtime.Serialization.ISerializable> interface to allow a class to control its serialization process.</span></span>  
  
### <a name="using-datacontractserializer"></a><span data-ttu-id="9ec78-110">使用 DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="9ec78-110">Using DataContractSerializer</span></span>  
  
- <span data-ttu-id="9ec78-111">所有加上 `[DataContract]` 屬性標記的型別必須是公用型別。</span><span class="sxs-lookup"><span data-stu-id="9ec78-111">All types marked with the `[DataContract]` attribute must be public.</span></span> <span data-ttu-id="9ec78-112">非公用型別無法在部分信任環境中進行序列化。</span><span class="sxs-lookup"><span data-stu-id="9ec78-112">Non-public types cannot be serialized in a partial trust environment.</span></span>  
  
- <span data-ttu-id="9ec78-113">可序列化之 `[DataContract]` 型別中的所有 `[DataContract]` 成員必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="9ec78-113">All `[DataContract]` members in a serializable `[DataContract]` type must be public.</span></span> <span data-ttu-id="9ec78-114">具有非公用 `[DataMember]` 的型別無法在部分信任環境中進行序列化。</span><span class="sxs-lookup"><span data-stu-id="9ec78-114">A type with a non-public `[DataMember]` cannot be serialized in a partial trust environment.</span></span>  
  
- <span data-ttu-id="9ec78-115">負責處理序列化事件 (例如，`OnSerializing`, `OnSerialized`、`OnDeserializing`，和 `OnDeserialized`) 的方法必須宣告為公用。</span><span class="sxs-lookup"><span data-stu-id="9ec78-115">Methods that handle serialization events (such as `OnSerializing`, `OnSerialized`, `OnDeserializing`, and `OnDeserialized`) must be declared as public.</span></span> <span data-ttu-id="9ec78-116">但是，同時支援 <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> 的明確與隱含實作。</span><span class="sxs-lookup"><span data-stu-id="9ec78-116">However, both explicit and implicit implementations of <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> are supported.</span></span>  
  
- <span data-ttu-id="9ec78-117">在標示為 `[DataContract]` 的組件中實作的 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 型別不可以在型別建構函式中執行安全性相關動作，因為 <xref:System.Runtime.Serialization.DataContractSerializer> 不會在還原序列化期間呼叫新產生物件的建構函式。</span><span class="sxs-lookup"><span data-stu-id="9ec78-117">`[DataContract]` types implemented in assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> must not perform security-related actions in the type constructor, as the <xref:System.Runtime.Serialization.DataContractSerializer> does not call the constructor of the newly-instantiated object during deserialization.</span></span> <span data-ttu-id="9ec78-118">具體來說，`[DataContract]` 型別必須避免使用下列常見的安全性技巧：</span><span class="sxs-lookup"><span data-stu-id="9ec78-118">Specifically, the following common security techniques must be avoided for `[DataContract]` types:</span></span>  
  
- <span data-ttu-id="9ec78-119">藉由將型別建構函式標示為內部或私用來嘗試限制部分信任存取。</span><span class="sxs-lookup"><span data-stu-id="9ec78-119">Attempting to restrict partial trust access by making the type's constructor internal or private.</span></span>  
  
- <span data-ttu-id="9ec78-120">藉由新增 `[LinkDemand]` 至型別建構函式來限制型別的存取。</span><span class="sxs-lookup"><span data-stu-id="9ec78-120">Restricting access to the type by adding a `[LinkDemand]` to the type's constructor.</span></span>  
  
- <span data-ttu-id="9ec78-121">假定因為物件已經成功產生，任何由建構函式所強制執行的驗證檢查也已通過。</span><span class="sxs-lookup"><span data-stu-id="9ec78-121">Assuming that because the object has been successfully instantiated, any validation checks enforced by the constructor have passed successfully.</span></span>  
  
### <a name="using-ixmlserializable"></a><span data-ttu-id="9ec78-122">使用 IXmlSerializable</span><span class="sxs-lookup"><span data-stu-id="9ec78-122">Using IXmlSerializable</span></span>  
 <span data-ttu-id="9ec78-123">下列最佳做法適用於可實作 <xref:System.Xml.Serialization.IXmlSerializable> 且可透過 <xref:System.Runtime.Serialization.DataContractSerializer> 進行序列化的型別：</span><span class="sxs-lookup"><span data-stu-id="9ec78-123">The following best practices apply for types that implement <xref:System.Xml.Serialization.IXmlSerializable> and are serialized using the <xref:System.Runtime.Serialization.DataContractSerializer>:</span></span>  
  
- <span data-ttu-id="9ec78-124"><xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> 靜態方法實作必須是 `public`。</span><span class="sxs-lookup"><span data-stu-id="9ec78-124">The <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> static method implementations must be `public`.</span></span>  
  
- <span data-ttu-id="9ec78-125">實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面的執行個體方法必須是 `public`。</span><span class="sxs-lookup"><span data-stu-id="9ec78-125">The instance methods that implement the <xref:System.Xml.Serialization.IXmlSerializable> interface must be `public`.</span></span>  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a><span data-ttu-id="9ec78-126">使用來自充分信任平台程式碼 (允許部分信任呼叫端的呼叫) 的 WCF</span><span class="sxs-lookup"><span data-stu-id="9ec78-126">Using WCF from Fully-Trusted Platform Code that Allows Calls from Partially Trusted Callers</span></span>  
 <span data-ttu-id="9ec78-127">WCF 部分信任安全性模型假設 WCF 公用方法或屬性的任何呼叫端在裝載的應用程式的程式碼存取安全性 (CAS) 內容中執行。</span><span class="sxs-lookup"><span data-stu-id="9ec78-127">The WCF partial trust security model assumes that any caller of a WCF public method or property is running in the code access security (CAS) context of the hosting application.</span></span> <span data-ttu-id="9ec78-128">WCF 也會假設每個都有該只有一個應用程式的安全性內容<xref:System.AppDomain>，且此內容在建立<xref:System.AppDomain>由受信任主應用程式的建立時間 (如藉由呼叫<xref:System.AppDomain.CreateDomain%2A>或 ASP.NET 應用程式管理員)。</span><span class="sxs-lookup"><span data-stu-id="9ec78-128">WCF also assumes that only one application security context exists for each <xref:System.AppDomain>, and that this context is established at <xref:System.AppDomain> creation time by a trusted host (for example, by a call to <xref:System.AppDomain.CreateDomain%2A> or by the ASP.NET Application Manager).</span></span>  
  
 <span data-ttu-id="9ec78-129">這個安全性模型適用於由使用者撰寫且無法判斷提示其他 CAS 權限的應用程式，例如在中度信任 ASP.NET 應用程式中執行的使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="9ec78-129">This security model applies to user-written applications that cannot assert additional CAS permissions, such as user code running in a Medium Trust ASP.NET application.</span></span> <span data-ttu-id="9ec78-130">不過，完全受信任的平台程式碼 （比方說，協力廠商組件安裝在全域組件快取，並接受來自部分信任程式碼呼叫） 時，必須考慮小心代表部分信任應用程式來呼叫 WCF避免應用程式層級安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="9ec78-130">However, fully-trusted platform code (for example, a third-party assembly that is installed in the global assembly cache and accepts calls from partially-trusted code) must take explicit care when calling into WCF on behalf of a partially-trusted application to avoid introducing application-level security vulnerabilities.</span></span>  
  
 <span data-ttu-id="9ec78-131">完全信任程式碼應該避免變更目前執行緒的 CAS 權限集合 (藉由呼叫<xref:System.Security.PermissionSet.Assert%2A>， <xref:System.Security.PermissionSet.PermitOnly%2A>，或<xref:System.Security.PermissionSet.Deny%2A>) 之前呼叫代表部分信任程式碼的 WCF Api。</span><span class="sxs-lookup"><span data-stu-id="9ec78-131">Full-trust code should avoid altering the CAS permission set of the current thread (by calling <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, or <xref:System.Security.PermissionSet.Deny%2A>) prior to calling WCF APIs on behalf of partially-trusted code.</span></span> <span data-ttu-id="9ec78-132">判斷提示、拒絕或以其他方式建立無關應用程式層級安全性內容的執行緒特定權限內容可能會導致未預期的行為。</span><span class="sxs-lookup"><span data-stu-id="9ec78-132">Asserting, denying, or otherwise creating a thread-specific permission context that is independent of the application-level security context can result in unexpected behavior.</span></span> <span data-ttu-id="9ec78-133">根據所使用的應用程式，這項行為可能會導致應用程式層級的安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="9ec78-133">Depending on the application, this behavior may result in application-level security vulnerabilities.</span></span>  
  
 <span data-ttu-id="9ec78-134">使用執行緒特定權限內容 WCF 呼叫必須準備好處理可能會發生下列情況的程式碼：</span><span class="sxs-lookup"><span data-stu-id="9ec78-134">Code that calls into WCF using a thread-specific permission context must be prepared to handle the following situations that may arise:</span></span>  
  
- <span data-ttu-id="9ec78-135">作業期間可能無法維護執行緒特定的安全性內容，進而導致可能發生的安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9ec78-135">The thread-specific security context may not be maintained for the duration of the operation, which results in potential security exceptions.</span></span>  
  
- <span data-ttu-id="9ec78-136">內部的 WCF 程式碼，以及任何使用者提供的回呼可能會比原始啟始呼叫所在的不同安全性內容中執行。</span><span class="sxs-lookup"><span data-stu-id="9ec78-136">Internal WCF code as well as any user-provided callbacks may run in a different security context than the one under which the call was originally initiated.</span></span> <span data-ttu-id="9ec78-137">這些內容包括：</span><span class="sxs-lookup"><span data-stu-id="9ec78-137">These contexts include:</span></span>  
  
    - <span data-ttu-id="9ec78-138">應用程式權限內容。</span><span class="sxs-lookup"><span data-stu-id="9ec78-138">The application permission context.</span></span>  
  
    - <span data-ttu-id="9ec78-139">任何先前由其他使用者使用執行緒來呼叫 WCF，目前正在執行的存留期間所建立的執行緒特定權限內容<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="9ec78-139">Any thread-specific permission context previously created by other user threads used to call into WCF during the lifetime of the currently running <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="9ec78-140">WCF 會保證部分信任程式碼無法取得完全信任權限，除非這類權限會判斷提示完全信任的元件之前呼叫 WCF 公用 Api。</span><span class="sxs-lookup"><span data-stu-id="9ec78-140">WCF guarantees that partially-trusted code cannot obtain full-trust permissions unless such permissions are asserted by a fully-trusted component prior to calling into WCF public APIs.</span></span> <span data-ttu-id="9ec78-141">但是，它不保證將完全信任的判斷提示影響隔離在特定執行緒、作業或使用者動作之外。</span><span class="sxs-lookup"><span data-stu-id="9ec78-141">However, it does not guarantee that the effects of asserting full trust is isolated to a particular thread, operation, or user action.</span></span>  
  
 <span data-ttu-id="9ec78-142">最佳做法是，避免呼叫 <xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.PermitOnly%2A> 或 <xref:System.Security.PermissionSet.Deny%2A> 來建立執行緒特定權限內容。</span><span class="sxs-lookup"><span data-stu-id="9ec78-142">As a best practice, avoid creating thread-specific permission context by calling <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, or <xref:System.Security.PermissionSet.Deny%2A>.</span></span> <span data-ttu-id="9ec78-143">反之，應該針對應用程式本身授與或拒絕權限，這樣就不會需要 <xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.Deny%2A> 或 <xref:System.Security.PermissionSet.PermitOnly%2A>。</span><span class="sxs-lookup"><span data-stu-id="9ec78-143">Instead, grant or deny the privilege to the application itself, so that no <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, or <xref:System.Security.PermissionSet.PermitOnly%2A> is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec78-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ec78-144">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
