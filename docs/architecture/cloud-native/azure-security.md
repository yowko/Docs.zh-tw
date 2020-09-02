---
title: 適用于雲端原生應用程式的 Azure 安全性
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |適用于雲端原生應用程式的 Azure 安全性
ms.date: 05/13/2020
ms.openlocfilehash: 7780b005d84124f202049deeb5be876364e6c5fa
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358969"
---
# <a name="azure-security-for-cloud-native-apps"></a>適用于雲端原生應用程式的 Azure 安全性

雲端原生應用程式可能比傳統應用程式更容易且更難以保護。 缺點在於，您需要保護更小的應用程式，並將更多的能源用於打造安全性基礎結構。 在大部分的服務部署中，程式設計語言和樣式的異類本質也表示您需要更留意來自許多不同提供者的安全性佈告欄。

另一方面，較小的服務，每個服務都有自己的資料存放區，可限制攻擊的範圍。 如果攻擊者入侵一個系統，攻擊者可能會比在整合型應用程式中更難跳到另一個系統。 進程界限是強式界限。 此外，如果資料庫備份流失，則損毀會更受限，因為該資料庫只包含一部分的資料，而且不太可能包含個人資料。

## <a name="threat-modeling"></a>威脅分析模型

無論這些優點是否超過雲端原生應用程式的缺點，都必須遵循相同的整體安全性思維。 安全性與安全思考必須屬於開發和操作案例的每個步驟。 規劃應用程式時，請詢問類似下列的問題：

- 這項資料遺失的影響為何？
- 如何將損毀資料的損害限制在這種服務中插入？
- 誰應該有此資料的存取權？
- 開發和發行程式是否有進行中的稽核原則？

上述所有問題都屬於稱為 [威脅分析模型](https://docs.microsoft.com/azure/security/azure-security-threat-modeling-tool)的程式。 此程式會嘗試回答系統發生什麼威脅、威脅的可能性，以及可能的損害。

一旦建立了威脅清單之後，您必須決定是否值得緩和。 有時候威脅是不太可能和昂貴的，因為它不太需要花能源來規劃。 例如，某些狀態層級動作專案可能會將變更插入數百萬個裝置所使用的進程設計。 現在，您不需要在 [ring 3](https://en.wikipedia.org/wiki/Protection_ring)中執行某段程式碼，而是在 ring 0 中執行該程式碼。 這可讓攻擊者略過虛擬程式，並在裸機機器上執行攻擊程式碼，以允許在該硬體上執行的所有虛擬機器上進行攻擊。

如果沒有 microscope 和深入瞭解該處理器的晶片設計，則難以偵測改變的處理器。 這種情況不太可能發生，且需要高昂資源才能減輕問題，因此可能不會有威脅模型建議您為其建立惡意探索保護。

更有可能的威脅（例如，中斷的存取控制允許 `Id` (`Id=2` `Id=3` 在 URL 中取代為) 或 SQL 插入式攻擊），對建立防護更具吸引力。 這些威脅的緩和措施相當合理，可建立及防止斑點公司信譽的尷尬安全性漏洞。

## <a name="principle-of-least-privilege"></a>最低權限原則

電腦安全性性的其中一項成立概念是 (POLP) 的最低許可權原則。 它實際上是以數位或實體形式的任何安全性形式的基本概念。 簡而言之，原則是任何使用者或進程都應該擁有最少的許可權來執行其工作。

例如，您可以考慮在銀行 tellers：存取 safe 是不尋常的活動。 因此，平均的出納無法開啟安全的本身。 若要取得存取權，他們需要透過銀行經理來提升其要求，以執行額外的安全性檢查。

在電腦系統中，有一個很棒的例子，就是使用者連接到資料庫的許可權。 在許多情況下，都有一個用來建立資料庫結構和執行應用程式的單一使用者帳戶。 除非在極端的情況下，執行應用程式的帳戶不需要更新架構資訊的能力。 應該會有數個帳戶提供不同層級的許可權。 應用程式只能使用授與資料表中資料之讀取和寫入存取權的許可權層級。 這種保護措施可以消除目標是卸載資料庫資料表或引入惡意觸發程式的攻擊。

幾乎每個建立雲端原生應用程式的部分，都可以從記住最低許可權的原則來獲益。 在以角色為基礎的存取控制中設定防火牆、網路安全性群組、角色和範圍 (RBAC) 時，可以找到它。

## <a name="penetration-testing"></a>滲透測試

隨著應用程式變得更複雜，攻擊媒介的數目會以驚人的速率增加。 威脅分析模型的瑕疵之處是，它通常是由建立系統的同一人所執行。 同樣地，許多開發人員都無法構思使用者互動，然後建立無法使用的使用者介面，大部分的開發人員都難以看到每個攻擊媒介。 建立系統的開發人員也有可能不太精通在攻擊方法中，也可能遺漏了重要的問題。

滲透測試或「觸控測試」牽涉到讓外部執行者嘗試攻擊系統。 這些攻擊者可能是外部諮詢公司或其他開發人員，其具有來自企業其他部分的良好安全性知識。 他們會獲得全權委託，以嘗試破壞系統。 他們經常會發現需要修補的廣泛安全性漏洞。 有時候攻擊的媒介將會是一項完全非預期的內容，像是針對 CEO 攻擊網路釣魚攻擊。

Azure 本身會不斷地從 [Microsoft 內的駭客團隊](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)進行攻擊。 多年來，他們已經成為找出數十個潛在的災難性攻擊媒介的第一種，在外部遭到惡意探索之前先加以關閉。 目標愈吸引人，永久性的動作專案會嘗試利用它，而世界上有幾個目標比 Azure 更有吸引力。

## <a name="monitoring"></a>監視

當攻擊者嘗試滲透應用程式時，應該會有一些警告。 通常，您可以藉由檢查服務的記錄來找出攻擊。 攻擊會離開各種跡象正負號，並在成功之前發現。 比方說，試圖猜測密碼的攻擊者會對登入系統提出許多要求。 在登入系統中進行監視，可以偵測出與一般存取模式不相關的奇怪模式。 這項監視可以轉換成警示，進而警示操作人員啟用某種類型的對策。 高度成熟的監視系統甚至可能會根據這些偏差主動新增規則來封鎖要求或節流回應，來採取行動。

## <a name="securing-the-build"></a>保護組建的安全

通常會忽略安全性的一個地方，就是建立程式。 不只是組建執行安全性檢查，像是掃描不安全的程式碼或簽入的認證，但組建本身應該是安全的。 如果組建伺服器遭到入侵，則會提供絕佳的向量，以將任意程式碼引入產品中。

假設攻擊者想要竊取登入 web 應用程式的使用者密碼。 他們可能會引進一個組建步驟來修改已簽出的程式碼，以將任何登入要求鏡像至另一部伺服器。 下一次執行程式碼時，它會以無訊息模式更新。 原始程式碼弱點掃描在組建之前執行時，不會攔截此程式碼。 同樣地，任何人都不會在程式碼審核中攔截，因為組建步驟會存留在組建伺服器上。 惡意探索的程式碼將會移至生產環境，讓它可以搜集密碼。 可能沒有組建程式變更的審核記錄，或至少沒有任何人監視該審核。

這是看似低價值目標的最佳範例，可用來中斷系統。 一旦攻擊者入侵系統的周邊，他們就可以開始著手找出將其許可權提升到其可能在任何地方造成真正損害的方式。

## <a name="building-secure-code"></a>建立安全的程式碼

.NET Framework 已經是相當安全的架構。 它可避免非受控碼的部分陷阱，例如結束陣列的結尾。 工作已積極完成，以修正探索到的安全性漏洞。 甚至還有一個 [bug 賞金方案](https://www.microsoft.com/msrc/bounty) ，可讓研究人員在架構中找出問題並加以報告，而不是利用這些問題。

有許多方式可讓 .NET 程式碼更安全。 下列指導方針（例如 .NET 文章的安全程式碼撰寫 [指導方針](../../standard/security/secure-coding-guidelines.md) ）是合理的步驟，可確保程式碼的安全。 [OWASP top 10](https://owasp.org/www-project-top-ten/)是建立安全程式碼的另一項有用的指南。

組建程式是一個不錯的位置，可讓掃描工具偵測原始程式碼中的問題，然後再使其進入生產環境。 大部分的專案都有某些其他封裝的相依性。 可掃描過期套件的工具將會在夜間組建中捕捉問題。 即使在建立 Docker 映射時，檢查並確定基底映射沒有已知弱點是很有用的。 另一個要檢查的事項是，沒有人不慎簽入認證。

## <a name="built-in-security"></a>內建安全性

Azure 的設計目的是為了平衡大多數使用者的可用性和安全性。 不同的使用者會有不同的安全性需求，因此需要微調其雲端安全性的方法。 Microsoft 在 [信任中心](https://azure.microsoft.com/support/trust-center/)發佈了大量的安全性資訊。 對於瞭解內建攻擊風險降低技術運作方式的專業人員而言，這項資源應該是第一次停止的人。

在 Azure 入口網站中， [Azure Advisor](https://azure.microsoft.com/services/advisor/) 是持續掃描環境並提出建議的系統。 其中一些建議是設計用來節省使用者的費用，但有些則是設計來識別可能不安全的設定，例如將儲存體容器開放給世界，而不受虛擬網路保護。

## <a name="azure-network-infrastructure"></a>Azure 網路基礎結構

在內部部署環境中，有許多能源是專門用來設定網路功能。 設定路由器、交換器和這類功能是很複雜的工作。 網路允許某些資源與其他資源通訊，並且在某些情況下防止存取。 常見的網路規則是限制從開發環境存取生產環境，而這可能會讓一半開發的程式碼執行困難並刪除 swath 的資料。

在現成的情況下，大部分的 PaaS Azure 資源都只會有最基本且寬鬆的網路設定。 比方說，網際網路上的任何人都可以存取 app service。 新的 SQL Server 實例通常會受到限制，因此，外部合作物件無法存取它們，但 Azure 本身所使用的 IP 位址範圍是由允許的。 因此，雖然 SQL server 受到外部威脅的保護，但攻擊者只需要設定 Azure 橋頭，讓他們能夠對 Azure 上的所有 SQL 實例發動攻擊。

幸好，大部分的 Azure 資源都可以放在 Azure 虛擬網路中，以允許更精細的存取控制。 類似于內部部署網路建立受到更廣泛保護之私人網路的方式，虛擬網路是位於 Azure 網路內的私人 IP 位址孤島。

![圖 9-1 Azure 中的虛擬網路](./media/virtual-network.png)

**圖 9-1**. Azure 中的虛擬網路。

和內部部署網路具有管理網路存取權的相同方式，您可以在虛擬網路的界限建立類似的防火牆。 根據預設，虛擬網路上的所有資源仍可與網際網路通訊。 這只是需要某種形式的明確防火牆例外的連入連線。

建立網路之後，就可以將儲存體帳戶之類的內部資源設定為只允許虛擬網路中的資源進行存取。 此防火牆可提供額外的安全性層級，如果該儲存體帳戶的金鑰洩漏，攻擊者就無法與其連線來入侵洩漏的金鑰。 這是最小許可權原則的另一個範例。

Azure Kubernetes 叢集中的節點可以參與虛擬網路，就像其他資源更是 Azure 的原生資源。 這項功能稱為「 [Azure 容器網路介面](https://github.com/Azure/azure-container-networking/blob/master/docs/cni.md)」。 實際上，它會在虛擬網路內配置用來配置虛擬機器和容器映射的子網。

繼續說明最低許可權原則的路徑，而不是虛擬網路內的每個資源都必須與其他每個資源溝通。 例如，在透過儲存體帳戶和 SQL database 提供 web API 的應用程式中，資料庫和儲存體帳戶不太可能需要彼此交談。 它們之間的任何資料共用都會經過 web 應用程式。 因此， [ (NSG) 的網路安全性群組 ](https://docs.microsoft.com/azure/virtual-network/security-overview) 可以用來拒絕兩個服務之間的流量。

拒絕資源之間通訊的原則可能會令人討厭，特別是在沒有流量限制的情況下使用 Azure 的背景。 在其他雲端上，網路安全性群組的概念更為普遍。 比方說，AWS 上的預設原則是，除非 NSG 中的規則啟用資源，否則資源無法彼此間的通訊。 雖然開發的速度較慢，但更嚴格的環境會提供更安全的預設值。 使用適當的 DevOps 做法（特別是使用 [Azure Resource Manager 或 Terraform](infrastructure-as-code.md) 來管理許可權），可讓您更輕鬆地控制規則。

在設定內部部署與雲端資源之間的通訊時，虛擬網路也會很有用。 虛擬私人網路可以用來將兩個網路順暢地連接在一起。 這可讓您在所有使用者都在現場的情況下，針對不具任何閘道的虛擬網路執行。 有一些技術可以用來建立此網路。 最簡單的方式是使用可在許多路由器和 Azure 之間建立的 [站對站 VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti) 。 流量會透過網際網路進行加密和通道傳送，且每個位元組的成本都與任何其他流量相同。 對於需要更多頻寬或更高安全性的案例，Azure 會提供一個稱為 [Express Route](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#ExpressRoute) 的服務，其使用內部部署網路與 Azure 之間的私人線路。 建立成本更高，但也更安全。

## <a name="role-based-access-control-for-restricting-access-to-azure-resources"></a>用來限制存取 Azure 資源的角色型存取控制

RBAC 是一種系統，可針對在 Azure 中執行的應用程式提供身分識別。 應用程式可以使用此身分識別來存取資源，而不是使用金鑰或密碼。

## <a name="security-principals"></a>安全性主體

RBAC 中的第一個元件是安全性主體。 安全性主體可以是使用者、群組、服務主體或受控識別。

![圖9-2 不同類型的安全性主體](./media/rbac-security-principal.png)

**圖 9-2**： 不同類型的安全性主體。

- 使用者-在 Azure Active Directory 中具有帳戶的任何使用者都是使用者。
- 群組-來自 Azure Active Directory 的使用者集合。 作為群組的成員，使用者除了自己的角色之外，還會取得該群組的角色。
- 服務主體-用來執行服務或應用程式的安全性識別。
- 受控識別-Azure 所管理的 Azure Active Directory 身分識別。 受控識別通常會在開發雲端應用程式時使用，這些應用程式會管理用來向 Azure 服務進行驗證的認證。

安全性主體可以套用至大部分的資源。 這表示您可以將安全性主體指派給在 Azure Kubernetes 內執行的容器，讓它能夠存取儲存在 Key Vault 中的秘密。 Azure 函式可能會採用許可權，讓它能夠與 Active Directory 實例交談，以驗證呼叫使用者的 JWT。 一旦使用服務主體啟用服務之後，就可以使用角色和範圍來更精確地管理其許可權。

## <a name="roles"></a>角色

安全性主體可採用許多角色，或使用更 sartorial 的比喻，也就是許多職。 每個角色會定義一系列的許可權，例如「從 Azure 服務匯流排端點讀取訊息」。 安全性主體的有效許可權集合是所有指派給安全性主體的所有角色之許可權的組合。 Azure 有大量的內建角色，且使用者可以定義自己的角色。

![圖 9-3 RBAC 角色定義](./media/rbac-role-definition.png)

**圖 9-3**。 RBAC 角色定義。

內建在 Azure 中也是許多高階角色，例如擁有者、參與者、讀者和使用者帳戶管理員。 使用「擁有者」角色時，安全性主體可以存取所有資源，並將許可權指派給其他人。 參與者具有與所有資源相同的存取層級，但無法指派許可權。 讀者只能查看現有的 Azure 資源，而使用者帳戶系統管理員可以管理對 Azure 資源的存取權。

更細微的內建角色（例如 [DNS 區域參與者](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#dns-zone-contributor) ）具有僅限單一服務的許可權。 安全性主體可採用任何數量的角色。

## <a name="scopes"></a>範圍

角色可套用至 Azure 內的一組受限制的資源。 例如，將範圍套用至先前從服務匯流排佇列讀取的範例，您可以將許可權縮小為單一佇列：「從 Azure 服務匯流排端點讀取訊息」 `blah.servicebus.windows.net/queue1`

範圍可以縮小為單一資源，也可以套用至整個資源群組、訂用帳戶或甚至是管理群組。

當測試安全性主體是否有特定許可權時，角色和範圍的組合將會列入考慮。 此組合提供強大的授權機制。

## <a name="deny"></a>Deny

之前，RBAC 只允許「允許」規則。 這種行為使某些範圍變得複雜。 例如，允許安全性主體存取所有的儲存體帳戶，但其中一個需要授與明確許可權給可能無止盡的儲存體帳戶清單。 每次建立新的儲存體帳戶時，都必須將其新增至此帳戶清單。 這種新增的管理額外負荷當然不太理想。

拒絕規則的優先順序高於允許規則。 現在代表相同的「允許全部但只允許一個」範圍，可表示為「全部允許」和「拒絕這個特定的」兩項規則。 拒絕規則不僅能簡化管理，還可讓您拒絕對每個人的存取，以提供額外安全的資源。

## <a name="checking-access"></a>檢查存取權

您可以想像，擁有大量的角色和範圍，可讓您找出服務主體的有效許可權相當困難。 堆積拒絕規則的基礎，只是為了提高複雜性。 幸運的是，有一個 [許可權計算機](https://docs.microsoft.com/azure/role-based-access-control/check-access) 可顯示任何服務主體的有效許可權。 它通常會在入口網站的 [IAM] 索引標籤下找到，如圖10-3 所示。

![圖 9-4 app service 的許可權計算機](./media/check-rbac.png)

**圖 9-4**。 App service 的許可權計算機。

## <a name="securing-secrets"></a>保護秘密

密碼和憑證是攻擊者常見的攻擊媒介。 密碼破解硬體可以進行暴力密碼破解攻擊，並嘗試每秒猜測數十億個密碼。 因此，用來存取資源的密碼很重要，因為有許多不同的字元。 這些密碼正是幾乎不可能記住的密碼類型。 幸運的是，Azure 中的密碼並不是任何人都必須知道的。

許多安全性 [專家都建議](https://www.troyhunt.com/password-managers-dont-have-to-be-perfect-they-just-have-to-be-better-than-not-having-one/) 使用密碼管理員來保存您自己的密碼是最好的方法。 雖然它會將您的密碼集中在一個位置，它也允許使用高度複雜的密碼，並確保每個帳戶都是唯一的。 相同的系統存在於 Azure 內：密碼的集中存放區。

## <a name="azure-key-vault"></a>Azure 金鑰保存庫

Azure Key Vault 提供集中的位置，以儲存資料庫、API 金鑰和憑證等專案的密碼。 一旦將秘密輸入至保存庫後，就不會再次顯示該秘密，而用來解壓縮和查看的命令會特意複雜。 Safe 中的資訊會使用軟體加密或 FIPS 140-2 Level 2 驗證的硬體安全性模組來保護。

金鑰保存庫的存取權是透過 Rbac 提供的，這表示不只有任何使用者都可以存取保存庫中的資訊。 假設 web 應用程式希望存取儲存在 Azure Key Vault 中的資料庫連接字串。 若要取得存取權，必須使用服務主體來執行應用程式。 在此假設的角色下，他們可以從 safe 讀取秘密。 有許多不同的安全性設定，可進一步限制應用程式對保存庫的存取權，使其無法更新秘密，但只能讀取密碼。

您可以監視金鑰保存庫的存取權，以確保只有預期的應用程式會存取保存庫。 記錄可以整合回 Azure 監視器，並在遇到未預期的情況時，解除鎖定設定警示的功能。

## <a name="kubernetes"></a>Kubernetes

在 Kubernetes 中，有一項類似的服務可維護少量的秘密資訊。 您可以透過一般可執行檔來設定 Kubernetes 秘密 `kubectl` 。

建立秘密就像尋找要儲存的 base64 版本值一樣簡單：

```console
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

然後將它新增至名為的秘密檔案，如 `secret.yml` 下列範例所示：

```yml
apiVersion: v1
kind: Secret
metadata:
  name: mysecret
type: Opaque
data:
  username: YWRtaW4=
  password: MWYyZDFlMmU2N2Rm
```

最後，您可以藉由執行下列命令，將此檔案載入至 Kubernetes：

```console
kubectl apply -f ./secret.yaml
```

然後可以將這些秘密掛接到磁片區，或透過環境變數對容器進程公開。 建立應用程式的 [十二要素應用](https://12factor.net/) 程式建議使用最低的一般分母將設定傳送至應用程式。 環境變數是最常見的分母，因為它們都受到支援，無論是作業系統或應用程式。

使用內建 Kubernetes 秘密的替代方法是從 Kubernetes 記憶體取 Azure Key Vault 中的密碼。 若要這麼做，最簡單的方式是將 RBAC 角色指派給想要載入秘密的容器。 然後，應用程式可以使用 Azure Key Vault Api 來存取秘密。 不過，這種方法需要修改程式碼，而不是遵循使用環境變數的模式。 相反地，您可以將值插入容器中。 這種方法比直接使用 Kubernetes 秘密更安全，因為它們可以由叢集上的使用者存取。

## <a name="encryption-in-transit-and-at-rest"></a>傳輸中和待用加密

無論資料位於不同服務之間的磁片或傳輸，都必須確保資料安全。 防止資料洩漏的最有效方式是將它加密為無法輕易讀取其他人的格式。 Azure 支援各種加密選項。

### <a name="in-transit"></a>傳輸中

有幾種方式可以在 Azure 中加密網路上的流量。 Azure 服務的存取通常是透過使用傳輸層安全性 (TLS) 的連線來完成。 例如，所有與 Azure Api 的連線都需要 TLS 連接。 同樣地，在 Azure 儲存體中與端點的連線只能透過 TLS 加密連接來運作。

TLS 是一種複雜的通訊協定，只是知道連線使用 TLS 並不是為了確保安全性。 比方說，TLS 1.0 chronically 不安全，TLS 1.1 的效能並不高。 即使在 TLS 的版本中，也有各種不同的設定可讓連接更容易解密。 最佳的作法是檢查伺服器連線是否使用最新且妥善設定的通訊協定。

這項檢查可由外部服務（例如 SSL 實驗室的 SSL 伺服器測試）來完成。 針對一般 Azure 端點的測試回合（在此案例中為服務匯流排端點）會產生接近完美的分數。

即使是 Azure SQL database 之類的服務也會使用 TLS 加密來防止資料被隱藏。 使用 TLS 加密傳輸中資料的有趣部分是，即使是 Microsoft，也無法接聽執行 TLS 之電腦之間的連線。 這應該可讓公司更輕鬆地瞭解其資料可能會有比標準攻擊者更多的資源，而可能會受到 Microsoft 的風險。

![圖9-5 顯示服務匯流排端點之分數的 SSL 實驗室報表。](./media/ssl-report.png)

**圖 9-5**。 顯示服務匯流排端點之分數的 SSL 實驗室報告。

雖然這一層級的加密不會讓所有時間都足夠，但它應該會對 Azure TLS 連線有相當安全的信賴度。 當加密改善時，Azure 將繼續發展其安全性標準。 很棒的一點是，有人會觀賞安全性標準，並在改善時更新 Azure。

### <a name="at-rest"></a>待用

在任何應用程式中，資料會在磁片上放置許多地方。 應用程式程式碼本身是從某些儲存機制載入的。 大部分的應用程式也會使用某種類型的資料庫，例如 SQL Server、Cosmos DB，甚至是非常的價格效益資料表儲存體。 這些資料庫都使用大量加密的儲存體，以確保具有適當許可權的應用程式以外的任何人都可以讀取您的資料。 即使系統操作員也無法讀取已加密的資料。 因此，客戶可以維持機密資訊的密碼資訊。

### <a name="storage"></a>儲存體

大部分的 Azure 都是 Azure 儲存體的引擎。 虛擬機器磁片會掛接在 Azure 儲存體上。 Azure Kubernetes Services 會在虛擬機器上執行，而這些虛擬機器本身裝載于 Azure 儲存體。 即使是無伺服器的技術（例如 Azure Functions Apps 和 Azure 容器實例），也是 Azure 儲存體中的磁碟空間來執行。

如果 Azure 儲存體妥善加密，則它會為大部分的其他專案提供基礎，也會進行加密。 Azure 儲存體 [會](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) 使用符合 [FIPS 140-2](https://en.wikipedia.org/wiki/FIPS_140) 規範的 [256 位 AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)進行加密。 這是一項知名的加密技術，在過去20年或多年來廣泛的學術審查主題。 目前沒有任何已知的實際攻擊，可讓某人不知道讀取 AES 加密的資料。

根據預設，用於加密 Azure 儲存體的金鑰是由 Microsoft 管理。 有廣泛的保護措施可確保防止惡意存取這些金鑰。 不過，具有特定加密需求的使用者也可以提供自己在 Azure Key Vault 中管理的 [儲存體金鑰](https://docs.microsoft.com/azure/storage/common/storage-encryption-keys-powershell) 。 您可以隨時撤銷這些金鑰，如此一來，就能有效轉譯儲存體帳戶的內容，使其無法存取。

虛擬機器使用加密的存放裝置，但您可以使用 Windows 上的 BitLocker 或 Linux 上的 DM Crypt 等技術，提供另一層加密。 這些技術的意思是，即使磁片映射的儲存空間已流失，仍可能接近無法讀取。

### <a name="azure-sql"></a>Azure SQL

裝載在 Azure SQL 上的資料庫會使用稱為 [透明資料加密 (TDE) ](/sql/relational-databases/security/encryption/transparent-data-encryption) 的技術，以確保資料保持加密。 預設會在所有新建立的 SQL 資料庫上啟用，但必須針對舊版資料庫手動啟用。 TDE 不只會執行資料庫的即時加密和解密，也會執行備份和交易記錄。

加密參數會儲存在資料庫中， `master` 而在啟動時，會將其餘作業讀入記憶體中。 這表示 `master` 資料庫必須保持未加密狀態。 實際的金鑰是由 Microsoft 管理。 不過，具有嚴格安全性需求的使用者可能會在 Key Vault 中提供自己的金鑰，就像對 Azure 儲存體所做的一樣。 Key Vault 針對這類服務提供金鑰輪替和撤銷。

TDS 的「透明」部分來自于不需要使用加密資料庫進行用戶端變更的事實。 雖然此方法可提供良好的安全性，但洩漏資料庫密碼足以讓使用者能夠解密資料。 另外還有另一種方法可加密資料庫中的個別資料行或資料表。 [Always Encrypted](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) 可確保加密資料不會以純文字顯示在資料庫內。

設定這一層的加密需要透過 SQL Server Management Studio 中的嚮導執行，以選取加密的排序，以及 Key Vault 中儲存相關聯金鑰的位置。

![圖9-6 選取要使用 Always Encrypted 加密之資料表中的資料行](./media/always-encrypted.png)

**圖 9-6**。 選取要使用 Always Encrypted 加密之資料表中的資料行。

從這些加密資料行讀取資訊的用戶端應用程式，必須提出特殊的額度才能讀取加密的資料。 連接字串必須以進行更新 `Column Encryption Setting=Enabled` ，而且必須從 Key Vault 取出用戶端認證。 接著，必須使用資料行加密金鑰可能遭受 SQL Server 用戶端。 完成之後，其餘的動作會使用 SQL 用戶端的標準介面。 也就是說，以 SQL 用戶端為基礎的 Dapper 和 Entity Framework 工具會繼續運作，而不需要變更。 每種語言的 Always Encrypted 可能尚未提供給每個 SQL Server 驅動程式使用。

TDE 和 Always Encrypted 的組合（兩者都可以搭配用戶端特定的金鑰使用）可確保即使是最嚴格的加密需求也是如此。

### <a name="cosmos-db"></a>Cosmos DB

Cosmos DB 是 Microsoft 在 Azure 中提供的最新資料庫。 它已從頭開始建立，並牢記安全性和密碼編譯。 AES 256 位加密對於所有 Cosmos DB 資料庫是標準的，而且無法停用。 結合 TLS 1.2 的通訊需求時，整個儲存體解決方案都會加密。

![圖 9-7 Cosmos DB 內的資料加密流程](./media/cosmos-encryption.png)

**圖 9-7**。 Cosmos DB 內的資料加密流程。

雖然 Cosmos DB 不會提供提供客戶加密金鑰，但小組已完成大量的工作，以確保它維持 PCI DSS 相容性。 Cosmos DB 也不支援任何類似 Azure SQL Always Encrypted 的單一資料行加密的方式。

## <a name="keeping-secure"></a>保持安全

Azure 具有發行高度安全產品所需的所有工具。 不過，連鎖的連結最弱。 如果部署在 Azure 上的應用程式不是以適當的安全性思維和良好的安全性審查來開發，則它們會成為鏈中的弱式連結。 有許多絕佳的靜態分析工具、加密庫和安全性作法，可用來確保 Azure 上所安裝的軟體與 Azure 本身一樣安全。 範例包括 [靜態分析工具](https://www.whitesourcesoftware.com/)、 [加密庫](https://www.libressl.org/)和 [安全性作法](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)。

>[!div class="step-by-step"]
>[上一個](security.md) 
>[下一步](devops.md)
