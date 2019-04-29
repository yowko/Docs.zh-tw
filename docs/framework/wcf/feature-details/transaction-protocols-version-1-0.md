---
title: 異動通訊協定 1.0 版
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: a1501bbd5364773359f9b62602ba4bb684f076ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764620"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="a2d89-102">異動通訊協定 1.0 版</span><span class="sxs-lookup"><span data-stu-id="a2d89-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="a2d89-103">Windows Communication Foundation (WCF) 第 1 版實作了 Ws-atomic Transaction 和 Ws-coordination 通訊協定 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="a2d89-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="a2d89-104">如需有關版本 1.1 的詳細資訊，請參閱[交易通訊協定](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="a2d89-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="a2d89-105">規格/文件</span><span class="sxs-lookup"><span data-stu-id="a2d89-105">Specification/Document</span></span>|<span data-ttu-id="a2d89-106">連結</span><span class="sxs-lookup"><span data-stu-id="a2d89-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="a2d89-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="a2d89-107">WS-Coordination</span></span>|<http://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|<span data-ttu-id="a2d89-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="a2d89-108">WS-AtomicTransaction</span></span>|<http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 <span data-ttu-id="a2d89-109">這些通訊協定規格的互通性需要滿足兩個層級：在應用程式之間，以及在異動管理員之間的層級 (請參閱下圖)。</span><span class="sxs-lookup"><span data-stu-id="a2d89-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="a2d89-110">規格詳細描述兩種互通性層級的訊息格式和訊息交換。</span><span class="sxs-lookup"><span data-stu-id="a2d89-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="a2d89-111">對應用程式之間的交換也會如同針對標準應用程式交換一樣，套用特定安全性、可靠性和編碼。</span><span class="sxs-lookup"><span data-stu-id="a2d89-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="a2d89-112">但是，交易管理員之間若要成功地達成互通性，便需要有一致的特定繫結，因為使用者通常不會設定它。</span><span class="sxs-lookup"><span data-stu-id="a2d89-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="a2d89-113">此主題描述 WS-Atomic 異動 (WS-AT) 安全性規格的組成，並且描述使用在異動管理員之間通訊的安全繫結程序。</span><span class="sxs-lookup"><span data-stu-id="a2d89-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="a2d89-114">本文件中描述的方法已經使用 WS-AT 和 WS-Coordination 的其他實作成功通過測試，其中包含 IBM、IONA、Sun Microsystems 和其他實作。</span><span class="sxs-lookup"><span data-stu-id="a2d89-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="a2d89-115">下圖說明兩個異動管理員，異動管理員 1 和異動管理員 2，與兩個應用程式，應用程式 1 和 2 應用程式之間的互通性：</span><span class="sxs-lookup"><span data-stu-id="a2d89-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![如果螢幕擷取畫面顯示交易之間的互動方式管理員。](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="a2d89-117">使用一個啟動器 (I) 和一個參與者 (P) 考量一般的 WS-Coordination/WS-Atomic Transaction 案例。</span><span class="sxs-lookup"><span data-stu-id="a2d89-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="a2d89-118">啟動器和參與者都有異動管理員 (分別是 ITM 和 PTM)。</span><span class="sxs-lookup"><span data-stu-id="a2d89-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="a2d89-119">在此主題中，兩階段交易認可會稱為 2PC。</span><span class="sxs-lookup"><span data-stu-id="a2d89-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a2d89-120">1.CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="a2d89-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="a2d89-121">12.應用程式訊息回應</span><span class="sxs-lookup"><span data-stu-id="a2d89-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="a2d89-122">2.CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="a2d89-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="a2d89-123">13.認可 (完成)</span><span class="sxs-lookup"><span data-stu-id="a2d89-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="a2d89-124">3.登錄 (完成)</span><span class="sxs-lookup"><span data-stu-id="a2d89-124">3. Register (Completion)</span></span>|<span data-ttu-id="a2d89-125">14.準備 (2PC)</span><span class="sxs-lookup"><span data-stu-id="a2d89-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="a2d89-126">4.RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="a2d89-126">4. RegisterResponse</span></span>|<span data-ttu-id="a2d89-127">15.準備 (2PC)</span><span class="sxs-lookup"><span data-stu-id="a2d89-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="a2d89-128">5.應用程式訊息</span><span class="sxs-lookup"><span data-stu-id="a2d89-128">5. Application Message</span></span>|<span data-ttu-id="a2d89-129">16.已準備 (2PC)</span><span class="sxs-lookup"><span data-stu-id="a2d89-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="a2d89-130">6.CreateCoordinationContext 搭配內容</span><span class="sxs-lookup"><span data-stu-id="a2d89-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="a2d89-131">17.已準備 (2PC)</span><span class="sxs-lookup"><span data-stu-id="a2d89-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="a2d89-132">7.註冊 (永久性)</span><span class="sxs-lookup"><span data-stu-id="a2d89-132">7. Register (Durable)</span></span>|<span data-ttu-id="a2d89-133">18.已認可 (完成)</span><span class="sxs-lookup"><span data-stu-id="a2d89-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="a2d89-134">8.RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="a2d89-134">8. RegisterResponse</span></span>|<span data-ttu-id="a2d89-135">19.認可 (2PC)</span><span class="sxs-lookup"><span data-stu-id="a2d89-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="a2d89-136">9.CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="a2d89-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="a2d89-137">20.認可 (2PC)</span><span class="sxs-lookup"><span data-stu-id="a2d89-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="a2d89-138">10.註冊 (永久性)</span><span class="sxs-lookup"><span data-stu-id="a2d89-138">10. Register (Durable)</span></span>|<span data-ttu-id="a2d89-139">21.已認可 (2PC)</span><span class="sxs-lookup"><span data-stu-id="a2d89-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="a2d89-140">11.RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="a2d89-140">11. RegisterResponse</span></span>|<span data-ttu-id="a2d89-141">22.已認可 (2PC)</span><span class="sxs-lookup"><span data-stu-id="a2d89-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="a2d89-142">此文件描述 WS-AtomicTransaction 安全性規格的組成，並且描述使用在異動管理員之間通訊的安全繫結程序。</span><span class="sxs-lookup"><span data-stu-id="a2d89-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="a2d89-143">本文件中描述的方法已經使用 WS-AT 和 WS-Coordination 的其他實作成功通過測試。</span><span class="sxs-lookup"><span data-stu-id="a2d89-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="a2d89-144">圖形與表格會從安全性觀點顯示四種訊息類別：</span><span class="sxs-lookup"><span data-stu-id="a2d89-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="a2d89-145">啟動訊息 (CreateCoordinationContext 和 CreateCoordinationContextResponse)。</span><span class="sxs-lookup"><span data-stu-id="a2d89-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="a2d89-146">登錄訊息 (Register 和 RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="a2d89-146">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="a2d89-147">通訊協定訊息 (準備、復原、認可和中止等等)。</span><span class="sxs-lookup"><span data-stu-id="a2d89-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="a2d89-148">應用程式訊息</span><span class="sxs-lookup"><span data-stu-id="a2d89-148">Application messages.</span></span>  
  
 <span data-ttu-id="a2d89-149">前三個訊息類別會視為異動管理員訊息，並且在此主題稍後的「應用程式訊息交換」中會描述其繫結程序組態。</span><span class="sxs-lookup"><span data-stu-id="a2d89-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="a2d89-150">第四個訊息類別是應用程式對應用程式訊息，並且在此主題稍後的「訊息範例」一節中會描述。</span><span class="sxs-lookup"><span data-stu-id="a2d89-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="a2d89-151">本章節描述使用這些類別的每個 WCF 的通訊協定繫結。</span><span class="sxs-lookup"><span data-stu-id="a2d89-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="a2d89-152">下列 XML 命名空間與關聯的前置詞會使用在整份文件中。</span><span class="sxs-lookup"><span data-stu-id="a2d89-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="a2d89-153">前置詞</span><span class="sxs-lookup"><span data-stu-id="a2d89-153">Prefix</span></span>|<span data-ttu-id="a2d89-154">命名空間 URI</span><span class="sxs-lookup"><span data-stu-id="a2d89-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="a2d89-155">s11</span><span class="sxs-lookup"><span data-stu-id="a2d89-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="a2d89-156">wsa</span><span class="sxs-lookup"><span data-stu-id="a2d89-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="a2d89-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="a2d89-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="a2d89-158">wsat</span><span class="sxs-lookup"><span data-stu-id="a2d89-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="a2d89-159">t</span><span class="sxs-lookup"><span data-stu-id="a2d89-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="a2d89-160">o</span><span class="sxs-lookup"><span data-stu-id="a2d89-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="a2d89-161">xsd</span><span class="sxs-lookup"><span data-stu-id="a2d89-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="a2d89-162">異動管理員繫結程序</span><span class="sxs-lookup"><span data-stu-id="a2d89-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="a2d89-163">R1001:異動管理員必須使用 SOAP 1.1 和 Ws-addressing 2004/08，Ws-atomic Transaction 和 Ws-coordination 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="a2d89-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="a2d89-164">應用程式訊息並不限於這些繫結，並且會在稍後描述。</span><span class="sxs-lookup"><span data-stu-id="a2d89-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="a2d89-165">異動管理員 HTTPS 繫結程序</span><span class="sxs-lookup"><span data-stu-id="a2d89-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="a2d89-166">異動管理員 HTTPS 繫結程序僅依賴傳輸安全性來達到安全性，並且在異動樹狀中的每個傳送者與接收者組之間建立信任。</span><span class="sxs-lookup"><span data-stu-id="a2d89-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="a2d89-167">HTTPS 傳輸組態</span><span class="sxs-lookup"><span data-stu-id="a2d89-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="a2d89-168">X.509 憑證會用來建立交易管理員身分識別。</span><span class="sxs-lookup"><span data-stu-id="a2d89-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="a2d89-169">需要用戶端/伺服器驗證，而用戶端/伺服器授權則留待實作詳細資料中說明：</span><span class="sxs-lookup"><span data-stu-id="a2d89-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="a2d89-170">R1111:透過網路提供的 X.509 憑證必須有符合起始電腦的完整的網域名稱 (FQDN) 的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="a2d89-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="a2d89-171">B1112:DNS 必須成功 X.509 主體名稱檢查系統中的每個傳送者與接收者組之間的功能。</span><span class="sxs-lookup"><span data-stu-id="a2d89-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="a2d89-172">啟動和登錄繫結組態</span><span class="sxs-lookup"><span data-stu-id="a2d89-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="a2d89-173">WCF 要求透過 HTTPS 的要求/回覆相互關聯的雙工繫結。</span><span class="sxs-lookup"><span data-stu-id="a2d89-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="a2d89-174">(如需有關相互關聯與要求/回覆訊息交換模式描述的詳細資訊，請參閱第 8 節的「WS-Atomic 交易」)。</span><span class="sxs-lookup"><span data-stu-id="a2d89-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="a2d89-175">2PC 通訊協定繫結組態</span><span class="sxs-lookup"><span data-stu-id="a2d89-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="a2d89-176">WCF 支援透過 HTTPS 的單向 （資料包） 訊息。</span><span class="sxs-lookup"><span data-stu-id="a2d89-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="a2d89-177">訊息間的相互關聯則留待實作詳細資料中說明。</span><span class="sxs-lookup"><span data-stu-id="a2d89-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="a2d89-178">B2131:實作必須支援`wsa:ReferenceParameters`Ws-addressing 達成的 WCF 的 2PC 訊息相互關聯所述。</span><span class="sxs-lookup"><span data-stu-id="a2d89-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="a2d89-179">異動管理員混合安全性繫結程序</span><span class="sxs-lookup"><span data-stu-id="a2d89-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="a2d89-180">這是替代 （混合模式） 繫結與身分識別建立目的的 Ws-coordination 發行權杖模型結合該使用傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="a2d89-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="a2d89-181">啟動與登錄是兩個繫結之間唯一不同的項目。</span><span class="sxs-lookup"><span data-stu-id="a2d89-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="a2d89-182">HTTPS 傳輸組態</span><span class="sxs-lookup"><span data-stu-id="a2d89-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="a2d89-183">X.509 憑證會用來建立交易管理員身分識別。</span><span class="sxs-lookup"><span data-stu-id="a2d89-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="a2d89-184">需要用戶端/伺服器驗證，而用戶端/伺服器授權則留待實作詳細資料中說明。</span><span class="sxs-lookup"><span data-stu-id="a2d89-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="a2d89-185">啟動訊息繫結組態</span><span class="sxs-lookup"><span data-stu-id="a2d89-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="a2d89-186">啟動訊息通常不會參與互通性，因為啟動訊息一般會發生在應用程式與其本機異動管理員之間。</span><span class="sxs-lookup"><span data-stu-id="a2d89-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="a2d89-187">B1221:WCF 會使用雙向 HTTPS 繫結 (中所述[傳訊通訊協定](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) 啟動訊息。</span><span class="sxs-lookup"><span data-stu-id="a2d89-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="a2d89-188">要求與回覆訊息會使用 WS-Addressing 2004/08 來相互關聯。</span><span class="sxs-lookup"><span data-stu-id="a2d89-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="a2d89-189">第 8 節的 WS-Atomic 異動規格進一步描述有關相互關聯與訊息交換模式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a2d89-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="a2d89-190">R1222:在收到`CreateCoordinationContext`，協調器必須發出`SecurityContextToken`與相關聯的祕密`STx`。</span><span class="sxs-lookup"><span data-stu-id="a2d89-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="a2d89-191">在符合 WS-Trust 規格的 `t:IssuedTokens` 標頭中會傳回這個權杖。</span><span class="sxs-lookup"><span data-stu-id="a2d89-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="a2d89-192">R1223:如果啟動發生在現有的協調內容`t:IssuedTokens`標頭`SecurityContextToken`聯現有的內容必須在流程`CreateCoordinationContext`訊息。</span><span class="sxs-lookup"><span data-stu-id="a2d89-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="a2d89-193">新`t:IssuedTokens`應產生標頭附加至傳出`wscoor:CreateCoordinationContextResponse`訊息。</span><span class="sxs-lookup"><span data-stu-id="a2d89-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="a2d89-194">登錄訊息繫結組態</span><span class="sxs-lookup"><span data-stu-id="a2d89-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="a2d89-195">B1231:WCF 會使用雙向 HTTPS 繫結 (中所述[傳訊通訊協定](../../../../docs/framework/wcf/feature-details/messaging-protocols.md))。</span><span class="sxs-lookup"><span data-stu-id="a2d89-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="a2d89-196">要求與回覆訊息會使用 WS-Addressing 2004/08 來相互關聯。</span><span class="sxs-lookup"><span data-stu-id="a2d89-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="a2d89-197">第 8 節的 WS-AtomicTransaction 進一步描述有關相互關聯與訊息交換模式描述的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a2d89-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="a2d89-198">R1232:外寄`wscoor:Register`必須使用訊息`IssuedTokenOverTransport`中所述的驗證模式[安全性通訊協定](../../../../docs/framework/wcf/feature-details/security-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="a2d89-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="a2d89-199">`wsse:Timestamp`項目必須使用簽署`SecurityContextToken STx`發出。</span><span class="sxs-lookup"><span data-stu-id="a2d89-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="a2d89-200">這個簽章是證明與特定異動關聯之權杖的所有權，並且用來驗證異動中登錄的參與者。</span><span class="sxs-lookup"><span data-stu-id="a2d89-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="a2d89-201">RegistrationResponse 訊息會透過 HTTPS 傳回。</span><span class="sxs-lookup"><span data-stu-id="a2d89-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="a2d89-202">2PC 通訊協定繫結組態</span><span class="sxs-lookup"><span data-stu-id="a2d89-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="a2d89-203">WCF 支援透過 HTTPS 的單向 （資料包） 訊息。</span><span class="sxs-lookup"><span data-stu-id="a2d89-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="a2d89-204">訊息間的相互關聯則留待實作詳細資料中說明。</span><span class="sxs-lookup"><span data-stu-id="a2d89-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="a2d89-205">B2131:實作必須支援`wsa:ReferenceParameters`Ws-addressing 達成的 WCF 的 2PC 訊息相互關聯所述。</span><span class="sxs-lookup"><span data-stu-id="a2d89-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="a2d89-206">應用程式訊息交換</span><span class="sxs-lookup"><span data-stu-id="a2d89-206">Application Message Exchange</span></span>  
 <span data-ttu-id="a2d89-207">應用程式可以隨意使用應用程式之間訊息的任何特定繫結程序，只要繫結程序符合下列安全性需求：</span><span class="sxs-lookup"><span data-stu-id="a2d89-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="a2d89-208">R2001:應用程式訊息必須流動`t:IssuedTokens`標頭與`CoordinationContext`訊息的標頭中。</span><span class="sxs-lookup"><span data-stu-id="a2d89-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="a2d89-209">R2002:完整性與機密性`t:IssuedToken`必須提供。</span><span class="sxs-lookup"><span data-stu-id="a2d89-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="a2d89-210">`CoordinationContext` 標頭包含 `wscoor:Identifier`。</span><span class="sxs-lookup"><span data-stu-id="a2d89-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="a2d89-211">雖然定義`xsd:AnyURI`允許使用絕對和相對 Uri，WCF 只支援`wscoor:Identifiers`，絕對 uri。</span><span class="sxs-lookup"><span data-stu-id="a2d89-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="a2d89-212">如果`wscoor:Identifier`的`wscoor:CoordinationContext`是相對 URI，異動的 WCF 服務會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2d89-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="a2d89-213">訊息範例</span><span class="sxs-lookup"><span data-stu-id="a2d89-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="a2d89-214">CreateCoordinationContext 要求/回應訊息</span><span class="sxs-lookup"><span data-stu-id="a2d89-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="a2d89-215">下列訊息會遵循要求/回應模式。</span><span class="sxs-lookup"><span data-stu-id="a2d89-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="a2d89-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="a2d89-216">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="a2d89-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="a2d89-217">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="a2d89-218">登錄訊息</span><span class="sxs-lookup"><span data-stu-id="a2d89-218">Registration Messages</span></span>  
 <span data-ttu-id="a2d89-219">下列訊息是登錄訊息。</span><span class="sxs-lookup"><span data-stu-id="a2d89-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="a2d89-220">登錄</span><span class="sxs-lookup"><span data-stu-id="a2d89-220">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="a2d89-221">註冊回應</span><span class="sxs-lookup"><span data-stu-id="a2d89-221">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="a2d89-222">兩階段交易認可通訊協定訊息</span><span class="sxs-lookup"><span data-stu-id="a2d89-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="a2d89-223">下列訊息與兩階段交易認可 (2PC) 通訊協定有關。</span><span class="sxs-lookup"><span data-stu-id="a2d89-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="a2d89-224">認可</span><span class="sxs-lookup"><span data-stu-id="a2d89-224">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="a2d89-225">應用程式訊息</span><span class="sxs-lookup"><span data-stu-id="a2d89-225">Application Messages</span></span>  
 <span data-ttu-id="a2d89-226">下列訊息是應用程式訊息。</span><span class="sxs-lookup"><span data-stu-id="a2d89-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="a2d89-227">應用程式訊息要求</span><span class="sxs-lookup"><span data-stu-id="a2d89-227">Application message-Request</span></span>  
  
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
