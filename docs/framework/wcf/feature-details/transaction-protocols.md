---
title: 傳輸通訊協定
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 60b9da567e8c82edf505a974c9884f6f1738747b
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066230"
---
# <a name="transaction-protocols"></a><span data-ttu-id="2ef60-102">傳輸通訊協定</span><span class="sxs-lookup"><span data-stu-id="2ef60-102">Transaction Protocols</span></span>
<span data-ttu-id="2ef60-103">Windows Communication Foundation (WCF) 會實作 Ws-atomic Transaction 和 Ws-coordination 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="2ef60-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="2ef60-104">規格/文件</span><span class="sxs-lookup"><span data-stu-id="2ef60-104">Specification/Document</span></span>|<span data-ttu-id="2ef60-105">版本</span><span class="sxs-lookup"><span data-stu-id="2ef60-105">Version</span></span>|<span data-ttu-id="2ef60-106">連結</span><span class="sxs-lookup"><span data-stu-id="2ef60-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="2ef60-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="2ef60-107">WS-Coordination</span></span>|<span data-ttu-id="2ef60-108">1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-108">1.0</span></span><br /><br /> <span data-ttu-id="2ef60-109">1.1</span><span class="sxs-lookup"><span data-stu-id="2ef60-109">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96104](https://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96079](https://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="2ef60-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="2ef60-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="2ef60-111">1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-111">1.0</span></span><br /><br /> <span data-ttu-id="2ef60-112">1.1</span><span class="sxs-lookup"><span data-stu-id="2ef60-112">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96080](https://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> https://go.microsoft.com/fwlink/?LinkId=96081|  
  
 <span data-ttu-id="2ef60-113">這些通訊協定規格的互通性需要滿足兩個層級：在應用程式之間，以及在異動管理員之間的層級 (請參閱下圖)。</span><span class="sxs-lookup"><span data-stu-id="2ef60-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="2ef60-114">規格詳細描述兩種互通性層級的訊息格式和訊息交換。</span><span class="sxs-lookup"><span data-stu-id="2ef60-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="2ef60-115">對應用程式之間的交換也會如同針對標準應用程式交換一樣，套用特定安全性、可靠性和編碼。</span><span class="sxs-lookup"><span data-stu-id="2ef60-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="2ef60-116">但是，交易管理員之間若要成功地達成互通性，便需要有一致的特定繫結，因為使用者通常不會設定它。</span><span class="sxs-lookup"><span data-stu-id="2ef60-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="2ef60-117">此主題描述 WS-Atomic 異動 (WS-AT) 安全性規格的組成，並且描述使用在異動管理員之間通訊的安全繫結程序。</span><span class="sxs-lookup"><span data-stu-id="2ef60-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="2ef60-118">本文件中描述的方法已經使用 WS-AT 和 WS-Coordination 的其他實作成功通過測試，其中包含 IBM、IONA、Sun Microsystems 和其他實作。</span><span class="sxs-lookup"><span data-stu-id="2ef60-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="2ef60-119">下圖描述兩個異動管理員之間：異動管理員 1 和異動管理員 2，以及兩個應用程式之間：應用程式 1 和應用程式 2 的互通性。</span><span class="sxs-lookup"><span data-stu-id="2ef60-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="2ef60-120">![異動通訊協定](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "異動管理員")</span><span class="sxs-lookup"><span data-stu-id="2ef60-120">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="2ef60-121">使用一個啟動器 (I) 和一個參與者 (P) 考量一般的 WS-Coordination/WS-Atomic Transaction 案例。</span><span class="sxs-lookup"><span data-stu-id="2ef60-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="2ef60-122">啟動器和參與者都有異動管理員 (分別是 ITM 和 PTM)。</span><span class="sxs-lookup"><span data-stu-id="2ef60-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="2ef60-123">在此主題中，兩階段交易認可會稱為 2PC。</span><span class="sxs-lookup"><span data-stu-id="2ef60-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ef60-124">1.CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="2ef60-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="2ef60-125">12.應用程式訊息回應</span><span class="sxs-lookup"><span data-stu-id="2ef60-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="2ef60-126">2.CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="2ef60-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="2ef60-127">13.認可 (完成)</span><span class="sxs-lookup"><span data-stu-id="2ef60-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="2ef60-128">3.登錄 (完成)</span><span class="sxs-lookup"><span data-stu-id="2ef60-128">3. Register (Completion)</span></span>|<span data-ttu-id="2ef60-129">14.準備 (2PC)</span><span class="sxs-lookup"><span data-stu-id="2ef60-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="2ef60-130">4.RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="2ef60-130">4. RegisterResponse</span></span>|<span data-ttu-id="2ef60-131">15.準備 (2PC)</span><span class="sxs-lookup"><span data-stu-id="2ef60-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="2ef60-132">5.應用程式訊息</span><span class="sxs-lookup"><span data-stu-id="2ef60-132">5. Application Message</span></span>|<span data-ttu-id="2ef60-133">16.已準備 (2PC)</span><span class="sxs-lookup"><span data-stu-id="2ef60-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="2ef60-134">6.CreateCoordinationContext 搭配內容</span><span class="sxs-lookup"><span data-stu-id="2ef60-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="2ef60-135">17.已準備 (2PC)</span><span class="sxs-lookup"><span data-stu-id="2ef60-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="2ef60-136">7.註冊 (永久性)</span><span class="sxs-lookup"><span data-stu-id="2ef60-136">7. Register (Durable)</span></span>|<span data-ttu-id="2ef60-137">18.已認可 (完成)</span><span class="sxs-lookup"><span data-stu-id="2ef60-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="2ef60-138">8.RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="2ef60-138">8. RegisterResponse</span></span>|<span data-ttu-id="2ef60-139">19.認可 (2PC)</span><span class="sxs-lookup"><span data-stu-id="2ef60-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="2ef60-140">9.CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="2ef60-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="2ef60-141">20.認可 (2PC)</span><span class="sxs-lookup"><span data-stu-id="2ef60-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="2ef60-142">10.註冊 (永久性)</span><span class="sxs-lookup"><span data-stu-id="2ef60-142">10. Register (Durable)</span></span>|<span data-ttu-id="2ef60-143">21.已認可 (2PC)</span><span class="sxs-lookup"><span data-stu-id="2ef60-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="2ef60-144">11.RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="2ef60-144">11. RegisterResponse</span></span>|<span data-ttu-id="2ef60-145">22.已認可 (2PC)</span><span class="sxs-lookup"><span data-stu-id="2ef60-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="2ef60-146">此文件描述 WS-AtomicTransaction 安全性規格的組成，並且描述使用在異動管理員之間通訊的安全繫結程序。</span><span class="sxs-lookup"><span data-stu-id="2ef60-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="2ef60-147">本文件中描述的方法已經使用 WS-AT 和 WS-Coordination 的其他實作成功通過測試。</span><span class="sxs-lookup"><span data-stu-id="2ef60-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="2ef60-148">圖形與表格會從安全性觀點顯示四種訊息類別：</span><span class="sxs-lookup"><span data-stu-id="2ef60-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="2ef60-149">啟動訊息 (CreateCoordinationContext 和 CreateCoordinationContextResponse)。</span><span class="sxs-lookup"><span data-stu-id="2ef60-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="2ef60-150">登錄訊息 (Register 和 RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="2ef60-150">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="2ef60-151">通訊協定訊息 (準備、復原、認可和中止等等)。</span><span class="sxs-lookup"><span data-stu-id="2ef60-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="2ef60-152">應用程式訊息</span><span class="sxs-lookup"><span data-stu-id="2ef60-152">Application messages.</span></span>  
  
 <span data-ttu-id="2ef60-153">前三個訊息類別會視為交易管理員訊息，並且在此主題稍後的「應用程式訊息交換」中會描述其繫結組態。</span><span class="sxs-lookup"><span data-stu-id="2ef60-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="2ef60-154">第四個訊息類別是應用程式對應用程式訊息，並且在此主題稍後的「訊息範例」一節中會描述。</span><span class="sxs-lookup"><span data-stu-id="2ef60-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="2ef60-155">本章節描述使用這些類別的每個 WCF 的通訊協定繫結。</span><span class="sxs-lookup"><span data-stu-id="2ef60-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="2ef60-156">下列 XML 命名空間與關聯的前置詞會使用在整份文件中。</span><span class="sxs-lookup"><span data-stu-id="2ef60-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="2ef60-157">前置詞</span><span class="sxs-lookup"><span data-stu-id="2ef60-157">Prefix</span></span>|<span data-ttu-id="2ef60-158">版本</span><span class="sxs-lookup"><span data-stu-id="2ef60-158">Version</span></span>|<span data-ttu-id="2ef60-159">命名空間 URI</span><span class="sxs-lookup"><span data-stu-id="2ef60-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="2ef60-160">s11</span><span class="sxs-lookup"><span data-stu-id="2ef60-160">s11</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96014](https://go.microsoft.com/fwlink/?LinkId=96014)|  
|<span data-ttu-id="2ef60-161">wsa</span><span class="sxs-lookup"><span data-stu-id="2ef60-161">wsa</span></span>|<span data-ttu-id="2ef60-162">Pre 1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="2ef60-163">1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-163">1.0</span></span>|http://www.w3.org/2004/08/addressing<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96022](https://go.microsoft.com/fwlink/?LinkId=96022)|  
|<span data-ttu-id="2ef60-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="2ef60-164">wscoor</span></span>|<span data-ttu-id="2ef60-165">1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-165">1.0</span></span><br /><br /> <span data-ttu-id="2ef60-166">1.1</span><span class="sxs-lookup"><span data-stu-id="2ef60-166">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96078](https://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96079](https://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="2ef60-167">wsat</span><span class="sxs-lookup"><span data-stu-id="2ef60-167">wsat</span></span>|<span data-ttu-id="2ef60-168">1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-168">1.0</span></span><br /><br /> <span data-ttu-id="2ef60-169">1.1</span><span class="sxs-lookup"><span data-stu-id="2ef60-169">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96080](https://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96081](https://go.microsoft.com/fwlink/?LinkId=96081)|  
|<span data-ttu-id="2ef60-170">t</span><span class="sxs-lookup"><span data-stu-id="2ef60-170">t</span></span>|<span data-ttu-id="2ef60-171">Pre-1.3</span><span class="sxs-lookup"><span data-stu-id="2ef60-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="2ef60-172">1.3</span><span class="sxs-lookup"><span data-stu-id="2ef60-172">1.3</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96082](https://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96100](https://go.microsoft.com/fwlink/?LinkId=96100)|  
|<span data-ttu-id="2ef60-173">o</span><span class="sxs-lookup"><span data-stu-id="2ef60-173">o</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96101](https://go.microsoft.com/fwlink/?LinkId=96101)|  
|<span data-ttu-id="2ef60-174">xsd</span><span class="sxs-lookup"><span data-stu-id="2ef60-174">xsd</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96102](https://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="2ef60-175">異動管理員繫結程序</span><span class="sxs-lookup"><span data-stu-id="2ef60-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="2ef60-176">R1001:參與 WS-AT 1.0 交易的交易管理員必須使用 SOAP 1.1 和 Ws-addressing 2004/08，Ws-atomic Transaction 和 Ws-coordination 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="2ef60-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="2ef60-177">R1002:參與 WS-AT 1.1 異動的異動管理員必須使用 SOAP 1.1 和 Ws-addressing 2005/08 Ws-atomic Transaction 和 Ws-coordination 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="2ef60-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="2ef60-178">應用程式訊息並不限於這些繫結，並且會在稍後描述。</span><span class="sxs-lookup"><span data-stu-id="2ef60-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="2ef60-179">交易管理員 HTTPS 繫結</span><span class="sxs-lookup"><span data-stu-id="2ef60-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="2ef60-180">交易管理員 HTTPS 繫結僅依賴傳輸安全性來達到安全性，並且在交易樹狀結構中的每個傳送者與接收者組之間建立信任。</span><span class="sxs-lookup"><span data-stu-id="2ef60-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="2ef60-181">HTTPS 傳輸組態</span><span class="sxs-lookup"><span data-stu-id="2ef60-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="2ef60-182">X.509 憑證會用來建立交易管理員身分識別。</span><span class="sxs-lookup"><span data-stu-id="2ef60-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="2ef60-183">需要用戶端/伺服器驗證，而用戶端/伺服器授權則留待實作詳細資料中說明：</span><span class="sxs-lookup"><span data-stu-id="2ef60-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="2ef60-184">R1111:透過網路提供的 X.509 憑證必須有符合起始電腦的完整的網域名稱 (FQDN) 的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="2ef60-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="2ef60-185">B1112:DNS 必須成功 X.509 主體名稱檢查系統中的每個傳送者與接收者組之間的功能。</span><span class="sxs-lookup"><span data-stu-id="2ef60-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="2ef60-186">啟動和登錄繫結組態</span><span class="sxs-lookup"><span data-stu-id="2ef60-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="2ef60-187">WCF 要求透過 HTTPS 的要求/回覆相互關聯的雙工繫結。</span><span class="sxs-lookup"><span data-stu-id="2ef60-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="2ef60-188">(如需有關相互關聯與要求/回覆訊息交換模式描述的詳細資訊，請參閱第 8 節的「WS-Atomic 異動」)。</span><span class="sxs-lookup"><span data-stu-id="2ef60-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="2ef60-189">2PC 通訊協定繫結組態</span><span class="sxs-lookup"><span data-stu-id="2ef60-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="2ef60-190">WCF 支援透過 HTTPS 的單向 （資料包） 訊息。</span><span class="sxs-lookup"><span data-stu-id="2ef60-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="2ef60-191">訊息間的相互關聯則留待實作詳細資料中說明。</span><span class="sxs-lookup"><span data-stu-id="2ef60-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="2ef60-192">B1131:實作必須支援`wsa:ReferenceParameters`Ws-addressing 達成的 WCF 的 2PC 訊息相互關聯所述。</span><span class="sxs-lookup"><span data-stu-id="2ef60-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="2ef60-193">交易管理員混合安全性繫結</span><span class="sxs-lookup"><span data-stu-id="2ef60-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="2ef60-194">這是個替代 (混合模式) 繫結，會針對識別建立目的同時使用傳輸安全性和 WS-Coordination 發行權杖模型。</span><span class="sxs-lookup"><span data-stu-id="2ef60-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="2ef60-195">啟動與登錄是兩個繫結之間唯一不同的項目。</span><span class="sxs-lookup"><span data-stu-id="2ef60-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="2ef60-196">HTTPS 傳輸組態</span><span class="sxs-lookup"><span data-stu-id="2ef60-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="2ef60-197">X.509 憑證會用來建立異動管理員身分識別。</span><span class="sxs-lookup"><span data-stu-id="2ef60-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="2ef60-198">需要用戶端/伺服器驗證，而用戶端/伺服器授權則留待實作詳細資料中說明。</span><span class="sxs-lookup"><span data-stu-id="2ef60-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="2ef60-199">啟動訊息繫結組態</span><span class="sxs-lookup"><span data-stu-id="2ef60-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="2ef60-200">啟動訊息通常不會參與互通性，因為啟動訊息一般會發生在應用程式與其本機異動管理員之間。</span><span class="sxs-lookup"><span data-stu-id="2ef60-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="2ef60-201">B1221:WCF 會使用雙向 HTTPS 繫結 (中所述[傳訊通訊協定](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) 啟動訊息。</span><span class="sxs-lookup"><span data-stu-id="2ef60-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="2ef60-202">要求與回覆訊息使用 WS-AT 1.0 的 WS-Addressing 2004/08 以及 WS-AT 1.1 的 WS-Addressing 2005/08 產生相互關聯。</span><span class="sxs-lookup"><span data-stu-id="2ef60-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="2ef60-203">第 8 節的 WS-Atomic 異動規格進一步描述有關相互關聯與訊息交換模式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2ef60-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="2ef60-204">R1222:在收到`CreateCoordinationContext`，協調器必須發出`SecurityContextToken`與相關聯的祕密`STx`。</span><span class="sxs-lookup"><span data-stu-id="2ef60-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="2ef60-205">在符合 WS-Trust 規格的 `t:IssuedTokens` 標頭中會傳回這個權杖。</span><span class="sxs-lookup"><span data-stu-id="2ef60-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="2ef60-206">R1223:如果啟動發生在現有的協調內容`t:IssuedTokens`標頭`SecurityContextToken`聯現有的內容必須在流程`CreateCoordinationContext`訊息。</span><span class="sxs-lookup"><span data-stu-id="2ef60-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="2ef60-207">新`t:IssuedTokens`應產生標頭附加至傳出`wscoor:CreateCoordinationContextResponse`訊息。</span><span class="sxs-lookup"><span data-stu-id="2ef60-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="2ef60-208">登錄訊息繫結組態</span><span class="sxs-lookup"><span data-stu-id="2ef60-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="2ef60-209">B1231:WCF 會使用雙向 HTTPS 繫結 (中所述[傳訊通訊協定](../../../../docs/framework/wcf/feature-details/messaging-protocols.md))。</span><span class="sxs-lookup"><span data-stu-id="2ef60-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="2ef60-210">要求與回覆訊息使用 WS-AT 1.0 的 WS-Addressing 2004/08 以及 WS-AT 1.1 的 WS-Addressing 2005/08 產生相互關聯。</span><span class="sxs-lookup"><span data-stu-id="2ef60-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="2ef60-211">第 8 節的 WS-AtomicTransaction 進一步描述有關相互關聯與訊息交換模式描述的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2ef60-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="2ef60-212">R1232:外寄`wscoor:Register`必須使用訊息`IssuedTokenOverTransport`中所述的驗證模式[安全性通訊協定](../../../../docs/framework/wcf/feature-details/security-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="2ef60-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="2ef60-213">`wsse:Timestamp`項目必須使用簽署`SecurityContextToken STx`發出。</span><span class="sxs-lookup"><span data-stu-id="2ef60-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="2ef60-214">這個簽章是證明與特定異動關聯之權杖的所有權，並且用來驗證異動中登錄的參與者。</span><span class="sxs-lookup"><span data-stu-id="2ef60-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="2ef60-215">RegistrationResponse 訊息會透過 HTTPS 傳回。</span><span class="sxs-lookup"><span data-stu-id="2ef60-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="2ef60-216">2PC 通訊協定繫結組態</span><span class="sxs-lookup"><span data-stu-id="2ef60-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="2ef60-217">WCF 支援透過 HTTPS 的單向 （資料包） 訊息。</span><span class="sxs-lookup"><span data-stu-id="2ef60-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="2ef60-218">訊息間的相互關聯則留待實作詳細資料中說明。</span><span class="sxs-lookup"><span data-stu-id="2ef60-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="2ef60-219">B1241:實作必須支援`wsa:ReferenceParameters`Ws-addressing 達成的 WCF 的 2PC 訊息相互關聯所述。</span><span class="sxs-lookup"><span data-stu-id="2ef60-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="2ef60-220">應用程式訊息交換</span><span class="sxs-lookup"><span data-stu-id="2ef60-220">Application Message Exchange</span></span>  
 <span data-ttu-id="2ef60-221">應用程式可以隨意使用應用程式之間訊息的任何特定繫結程序，只要繫結程序符合下列安全性需求：</span><span class="sxs-lookup"><span data-stu-id="2ef60-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="2ef60-222">R2001:應用程式訊息必須流動`t:IssuedTokens`標頭與`CoordinationContext`訊息的標頭中。</span><span class="sxs-lookup"><span data-stu-id="2ef60-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="2ef60-223">R2002:完整性與機密性`t:IssuedToken`必須提供。</span><span class="sxs-lookup"><span data-stu-id="2ef60-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="2ef60-224">`CoordinationContext` 標頭包含 `wscoor:Identifier`。</span><span class="sxs-lookup"><span data-stu-id="2ef60-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="2ef60-225">雖然定義`xsd:AnyURI`允許使用絕對和相對 Uri，WCF 只支援`wscoor:Identifiers`，絕對 uri。</span><span class="sxs-lookup"><span data-stu-id="2ef60-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="2ef60-226">B2003:如果`wscoor:Identifier`的`wscoor:CoordinationContext`是相對 URI，異動的 WCF 服務會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="2ef60-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="2ef60-227">訊息範例</span><span class="sxs-lookup"><span data-stu-id="2ef60-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="2ef60-228">CreateCoordinationContext 要求/回應訊息</span><span class="sxs-lookup"><span data-stu-id="2ef60-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="2ef60-229">下列訊息會遵循要求/回應模式。</span><span class="sxs-lookup"><span data-stu-id="2ef60-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="2ef60-230">CreateCoordinationContext 搭配 WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="2ef60-231">CreateCoordinationContext 搭配 WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="2ef60-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>   
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
<a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
<a:ReplyTo>   
<Address>https://...</a:Address>   
</a:ReplyTo>   
<a:To>https://...</a:To>   
<wsse:Security>  
 <u:Timestamp>  
<wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
<wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
</u:Timestamp>   
</wsse:Security>   
</s:Header>   
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
<wscoor:CreateCoordinationContext>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
</wscoor:CreateCoordinationContext>  
 </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="2ef60-232">CreateCoordinationContextResponse 搭配 Trust Pre-1.3 和 WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse     
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>   
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>    
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference   
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference   
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret   
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="2ef60-233">CreateCoordinationContextResponse 搭配 Trust 1.3 和 WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="2ef60-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->   
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>   
<t:IssuedTokens>   
<wst:RequestSecurityTokenResponse   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"  
xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>   
<wsc:SecurityContextToken>   
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>   
</wsc:SecurityContextToken>   
</wst:RequestedSecurityToken>   
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
<wst:RequestedAttachedReference>   
<wsse:SecurityTokenReference >   
<wsse:Reference  
  ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
  URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</wst:RequestedAttachedReference>   
<wst:RequestedUnattachedReference>   
<wsse:SecurityTokenReference>   
<wsse:Reference  
 ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
 URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</wst:RequestedUnattachedReference>   
<wst:RequestedProofToken>   
<wst:BinarySecret  
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
  <!-- base64 encoded value -->   
</wst:BinarySecret>   
</wst:RequestedProofToken>   
<wst:Lifetime>   
<wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
<wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
</wst:Lifetime>   
<wst:KeySize>256</wst:KeySize>   
</wst:RequestSecurityTokenResponse>   
</t:IssuedTokens>   
<o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">   
<u:Timestamp u:Id="_0">   
<u:Created>2005-12-15T23:36:12.015Z</u:Created>   
<u:Expires>2005-12-15T23:41:12.015Z</u:Expires>   
</u:Timestamp>   
</o:Security>   
</s:Header>   
<s:Body>   
<wscoor:CreateCoordinationContextResponse>   
<wscoor:CoordinationContext>   
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>   
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>   
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>   
</wscoor:CoordinationContext>   
</wscoor:CreateCoordinationContextResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="2ef60-234">登錄訊息</span><span class="sxs-lookup"><span data-stu-id="2ef60-234">Registration Messages</span></span>  
 <span data-ttu-id="2ef60-235">下列訊息是登錄訊息。</span><span class="sxs-lookup"><span data-stu-id="2ef60-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="2ef60-236">登錄 wscoor 1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-236">Register with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>        
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference   
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="2ef60-237">登錄 WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="2ef60-237">Register with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>   
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
<a:ReplyTo>   
<a:Address>https://...</a:Address>   
</a:ReplyTo>  
<a:To>https://...</a:To>   
<wsse:Security   
s:mustUnderstand="1"   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wssu:Timestamp wssu:Id="_0" >   
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>   
<wsc:SecurityContextToken>   
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>   
</wsc:SecurityContextToken>   
<!-- supporting signature over the timestamp -->  
<wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
<ds:SignedInfo>   
<ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>   
<ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>   
<ds:Reference URI="#_0">   
<ds:Transforms>   
<ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>   
</ds:Transforms>   
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>   
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>   
</ds:Reference>   
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>   
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</ds:KeyInfo>   
</wsse:Signature>   
</wsse:Security>   
</s:Header>   
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">   
<wscoor:Register>   
<wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
<wscoor:ParticipantProtocolService>   
<a:Address>https://... </a:Address>  
</wscoor:ParticipantProtocolService>   
</wscoor:Register>   
</s:Body>   
</s:Envelope>  
```  
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="2ef60-238">登錄回應 wscoor 1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-238">Register Response with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e        
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="2ef60-239">登錄回應 WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="2ef60-239">Register Response with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>   
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
<a:To>https://...</a:To>   
<wsse:Security   
s:mustUnderstand="1"   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">   
<wssu:Timestamp>   
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>   
</wsse:Security>   
</s:Header>   
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">   
<wscoor:RegisterResponse>   
<wscoor:CoordinatorProtocolService>  
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>   
</wscoor:RegisterResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="2ef60-240">兩階段交易認可通訊協定訊息</span><span class="sxs-lookup"><span data-stu-id="2ef60-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="2ef60-241">下列訊息與兩階段交易認可 (2PC) 通訊協定有關。</span><span class="sxs-lookup"><span data-stu-id="2ef60-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="2ef60-242">認可 wsat 1.0</span><span class="sxs-lookup"><span data-stu-id="2ef60-242">Commit with WSAT 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="2ef60-243">認可 WSAT 1.1</span><span class="sxs-lookup"><span data-stu-id="2ef60-243">Commit with WSAT 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
<a:To>https://...</a:To>   
<wsse:Security   
s:mustUnderstand="1"   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">   
<wssu:Timestamp wssu:Id="_0" >   
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>   
</wsse:Security>   
</s:Header>   
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">   
<wsat:Commit />   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="2ef60-244">應用程式訊息</span><span class="sxs-lookup"><span data-stu-id="2ef60-244">Application Messages</span></span>  
 <span data-ttu-id="2ef60-245">下列訊息是應用程式訊息。</span><span class="sxs-lookup"><span data-stu-id="2ef60-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="2ef60-246">應用程式訊息要求</span><span class="sxs-lookup"><span data-stu-id="2ef60-246">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">   
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken   
          wssu:Id="IA_Certificate"   
          ValueType="...#X509v3"   
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->    
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader   
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->      
    <e:EncryptedData Id="encrypted_body"   
           Type="http://www.w3.org/2001/04/xmlenc#Content"   
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
