---
title: 適用于雲端原生應用程式的 Azure 安全性
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |適用于雲端原生應用程式的 Azure 安全性
ms.date: 06/30/2019
ms.openlocfilehash: 79e1ec9bd91285041791e36275b03f128f2fe136
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183606"
---
# <a name="azure-security-for-cloud-native-apps"></a>適用于雲端原生應用程式的 Azure 安全性

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

與傳統應用程式相比，雲端原生應用程式可以更輕鬆且更容易受到保護。 就缺點而言，您必須保護更小的應用程式，並將更多的能源用於建立安全性基礎結構。 在大部分服務部署中，程式設計語言和樣式的本質上，也表示您需要特別注意來自許多不同提供者的安全性佈告欄。 

另一方面，較小的服務（每個都有自己的資料存放區）會限制攻擊的範圍。 如果攻擊者危害一個系統，攻擊者可能會更難以跳到另一個系統，而不是在整合型應用程式中。 進程界限是強式界限。 此外，如果資料庫備份流失，則損毀會更有限制，因為該資料庫只包含資料的子集，而且不太可能包含個人資料。

## <a name="threat-modeling"></a>威脅模型化

無論優點是否超過雲端原生應用程式的缺點，都必須遵循相同的整體安全性思維。 安全性和安全思考必須屬於開發和營運案例的每個步驟。 在規劃應用程式時，請詢問下列問題：

* 這項資料遺失的影響為何？
* 如何限制插入此服務的錯誤資料損毀？
* 誰應該擁有此資料的存取權？
* 有關于開發和發行程式的稽核原則嗎？

這些問題都是一個稱為[威脅模型](https://docs.microsoft.com/azure/security/azure-security-threat-modeling-tool)化程式的一部分。 此程式會嘗試回答問題，其中包括系統的威脅、威脅的可能性，以及可能的損害。 

一旦建立了威脅清單之後，您必須決定是否值得緩和。 有時候威脅的代價不高，因此不太可能需要花費能源來進行規劃。 比方說，某些狀態層級動作專案可能會將變更插入至數百萬個裝置所使用之進程的設計。 現在，我們不會在[環 3](https://en.wikipedia.org/wiki/Protection_ring)中執行特定的程式碼，而是在 ring 0 中執行該程式碼。 這可讓惡意探索略過虛擬機器，並在裸機機器上執行攻擊程式碼，以允許在該硬體上執行的所有虛擬機器上進行攻擊。

更改過的處理器在沒有 microscope 的情況下，很容易偵測到該處理器的晶片設計上有其深入知識。 這種情況不太可能發生，降低成本，因此可能沒有威脅模型會建議為它建立惡意探索保護。 

較可能的威脅（例如，中斷的訪問`Id`控制允許增量攻擊`Id=2` （ `Id=3`以 URL 取代為）或 SQL 插入式，對於建立保護更為吸引人。 這些威脅的緩和措施相當合理，可以建立並防止斑點公司信譽的尷尬安全性漏洞。 

## <a name="principle-of-least-privilege"></a>最低許可權原則

電腦安全性性的一項初步概念是最低許可權（POLP）的原則。 它實際上是任何形式安全性的基本概念，也就是數位或實體。 簡而言之，原則是任何使用者或程式都應該擁有最少的許可權來執行其工作。 

例如，假設有一個銀行的出納員：存取 safe 是不尋常的活動。 因此，平均取款無法自行開啟安全。 若要取得存取權，他們必須透過負責執行額外安全性檢查的銀行經理來提升其要求。 

在電腦系統中，很棒的例子就是連接到資料庫的使用者權限。 在許多情況下，都有一個用來建立資料庫結構和執行應用程式的單一使用者帳戶。 除了在極端情況下，執行應用程式的帳戶不需要更新架構資訊的能力。 應該有數個帳戶可提供不同層級的許可權。 應用程式應該只使用授與讀取和寫入權限給資料表中之資料的許可權層級。 這種保護措施可以排除目標為卸載資料庫資料表或引進惡意觸發程式的攻擊。 

幾乎每個建立雲端原生應用程式的部分都可以因記住最低許可權的原則而受益。 在角色型存取控制（RBAC）中設定防火牆、網路安全性群組、角色和範圍時，您可以在播放時找到它。

## <a name="penetration-testing"></a>滲透測試

隨著應用程式變得更複雜，攻擊媒介的數目也會以驚人的速率增加。 威脅分析模型的缺陷在於，它通常是由同一個建立系統的人員所執行。 就像許多開發人員在構思使用者互動，然後建立無法使用的使用者介面一樣，大部分的開發人員都難以看到每個攻擊的向量。 建立系統的開發人員也可能無法在攻擊方法中精通，而且也錯過了重要的事。 

滲透測試或「畫筆測試」牽涉到外部執行者嘗試攻擊系統。 這些攻擊者可能是外部諮詢公司或其他開發人員，從企業的其他部分獲得良好的安全性知識。 他們會提供全權委託來嘗試破壞系統。 它們經常會發現需要修補的大量安全性漏洞。 有時候，攻擊向量將會是完全非預期的東西，像是利用對 CEO 的網路釣魚攻擊。

Azure 本身會持續從[Microsoft 內部的駭客小組](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)進行攻擊。 多年來，他們一直以來都是找出數十個潛在的嚴重攻擊媒介，先將它們關閉後再從外部惡意探索。 目標越吸引人，永久性的執行者會嘗試利用它，而且在世界上有幾個目標比 Azure 更有吸引力。 

## <a name="monitoring"></a>監視

如果攻擊者嘗試滲透應用程式，應該會有一些警告。 通常，您可以藉由檢查服務的記錄來找出攻擊。 攻擊會留下可在成功前發現的各種跡象徵兆。 比方說，嘗試猜測密碼的攻擊者會對登入系統發出許多要求。 以登入系統為中心的監視可以偵測出與一般存取模式不相關的奇怪模式。 這項監視可以轉換成警示，進而提醒作業人員啟用某種類型的對策。 高度成熟的監視系統甚至可能會根據這些偏差主動新增規則來封鎖要求或節流回應，而採取動作。 

## <a name="securing-the-build"></a>保護組建

通常會忽略安全性的一個位置，就是在建立程式的過程中。 不只應該組建執行安全性檢查，例如掃描不安全的程式碼或簽入認證，但組建本身應該是安全的。 如果組建伺服器遭到入侵，它會提供絕佳的向量，讓您將任意程式碼引進產品中。 

想像一下，攻擊者想要竊取登入 web 應用程式的使用者密碼。 他們可能會引進一個組建步驟，修改已簽出的程式碼，以將任何登入要求鏡像至另一部伺服器。 下一次程式碼完成組建時，它會以無訊息模式更新。 原始程式碼弱點掃描不會在組建之前執行，因此不會攔截此程式碼。 同樣地，任何人都不會在程式碼審核中攔截它，因為組建伺服器上有即時的組建步驟。 被利用的程式碼會進入生產環境，讓它能夠收集密碼。 可能不會有任何組建程式變更的 audit 記錄檔，或至少沒有任何人監控該 audit。 

這是看似低價值目標的最佳範例，可以用來中斷系統。 一旦攻擊者入侵系統的周邊，他們就可以開始找出方法，將其許可權提升到他們想要的任何地方都可能造成真正的傷害。

## <a name="building-secure-code"></a>建立安全的程式碼

.NET Framework 已經是非常安全的架構。 它可避免非受控碼的某些陷阱，例如離開陣列的結尾。 致力於在發現安全性漏洞時進行修正。 甚至還有一個[bug 豐富程式](https://www.microsoft.com/msrc/bounty)，可讓研究人員找出架構中的問題並回報，而不是利用它們。 

有許多方法可讓 .NET 程式碼更安全。 遵循適用于 .NET 的[安全](https://docs.microsoft.com/dotnet/standard/security/secure-coding-guidelines)程式碼撰寫方針一文的指導方針，是確保程式碼從頭開始安全的合理步驟。 [OWASP 前10名](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_2017_Project)是建立安全程式碼的另一個寶貴指南。

建立程式是放置掃描工具以偵測原始程式碼中的問題，再使其進入生產環境的最佳位置。 大部分的專案都會相依于某些其他封裝。 可以掃描過時套件的工具，將會在夜間組建中攔截問題。 即使在建立 Docker 映射時，檢查並確定基底映射並不會有已知的弱點，會很有説明。 另一個要檢查的事項是沒有人不慎簽入認證。 

## <a name="built-in-security"></a>內建安全性 

Azure 的設計是為了平衡大部分使用者的可用性和安全性。 不同的使用者會有不同的安全性需求，因此他們需要微調其雲端安全性的方法。 Microsoft 在[信任中心](https://azure.microsoft.com/support/trust-center/)發佈了大量的安全性資訊。 對於想要瞭解內建攻擊緩和技術如何工作的專業人員，這項資源應該是第一次停止。

在 Azure 入口網站內， [Azure Advisor](https://azure.microsoft.com/services/advisor/)是持續掃描環境並提出建議的系統。 其中一些建議是為了節省使用者的金錢而設計，但其他則是設計來識別可能不安全的設定，例如讓儲存體容器開放給世界，而不受虛擬網路保護。

## <a name="azure-network-infrastructure"></a>Azure 網路基礎結構

在內部部署環境中，有一項絕佳的能源是專門用來設定網路功能。 設定路由器、交換器和這類工作是複雜的工作。 網路可讓特定資源與其他資源通訊，並在某些情況下防止存取。 經常的網路規則是限制從開發環境存取生產環境的機會，因為這會造成一半開發的程式碼執行困難並刪除資料 swath。

在預設情況下，大部分的 PaaS Azure 資源僅具有最基本和寬鬆的網路設定。 例如，網際網路上的任何人都可以存取應用程式服務。 新的 SQL Server 實例通常會受到限制，因此外部方無法存取它們，但 Azure 本身所使用的 IP 位址範圍則是允許的。 因此，雖然 SQL server 受到外部威脅的保護，但攻擊者只需要設定 Azure 橋頭，讓他們能夠對 Azure 上的所有 SQL 實例發動攻擊。

幸好，大部分的 Azure 資源都可以放入 Azure 虛擬網路，以允許更精細的存取控制。 與內部部署網路建立從較大世界保護之私人網路的方式類似，虛擬網路是位於 Azure 網路內的私人 IP 位址孤島。

![圖 10-1 Azure](./media/virtual-network.png)
**圖 10-1**中的虛擬網路。 Azure 中的虛擬網路。

與內部部署網路有防火牆管理網路存取的相同方式，您可以在虛擬網路的界限建立類似的防火牆。 根據預設，虛擬網路上的所有資源仍可與網際網路通訊。 這只是需要某種形式的明確防火牆例外的連入連線。

建立網路之後，就可以將儲存體帳戶之類的內部資源設定為只允許也在虛擬網路上的資源存取。 此防火牆會提供額外的安全性等級，如果該儲存體帳戶的金鑰洩露，攻擊者就無法連線到它來入侵洩露的金鑰。 這是最低許可權原則的另一個範例。

Azure Kubernetes 叢集中的節點可以參與虛擬網路，就像其他 Azure 的原生資源一樣。 這種功能稱為[Azure Container 網路介面](https://github.com/Azure/azure-container-networking/blob/master/docs/cni.md)。 實際上，它會在虛擬網路內配置虛擬機器和容器映射所要配置的子網。

繼續說明最低許可權原則的路徑，而不是虛擬網路中的每個資源都必須與其他資源溝通。 比方說，在透過儲存體帳戶和 SQL 資料庫提供 Web API 的應用程式中，資料庫和儲存體帳戶不太可能需要彼此通訊。 它們之間的任何資料共用都會經過 web 應用程式。 因此，[網路安全性群組（NSG）](https://docs.microsoft.com/azure/virtual-network/security-overview)可用來拒絕這兩個服務之間的流量。

拒絕資源間通訊的原則可能會令人討厭，特別是來自使用 Azure 的背景，而不會有流量限制。 在某些其他雲端上，網路安全性群組的概念更為普遍。 例如，AWS 上的預設原則是資源無法彼此通訊，直到 NSG 中的規則啟用為止。 雖然開發的速度較慢，但更嚴格的環境會提供更安全的預設值。 使用適當的 DevOps 做法，特別是使用[Azure Resource Manager 或 Terraform](infrastructure-as-code.md)來管理許可權，可以讓您更輕鬆地控制規則。

在設定內部部署與雲端資源之間的通訊時，虛擬網路也很有用。 虛擬私人網路可用來將兩個網路緊密地連結在一起。 這可讓您在所有使用者都在現場的案例中，執行沒有任何閘道的虛擬網路。 有一些技術可以用來建立此網路。 最簡單的是使用可在許多路由器和 Azure 之間建立的[站對站 VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti) 。 流量會透過網際網路進行加密，並以每個位元組的相同成本與任何其他流量進行通道處理。 針對需要更多頻寬或更多安全性的案例，Azure 提供了一種稱為「[快速路由](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#ExpressRoute)」的服務，其使用內部部署網路與 Azure 之間的私用電路。 成本更高且難以建立，但也更安全。 

## <a name="role-based-access-control-for-restricting-access-to-azure-resources"></a>用於限制 Azure 資源存取權的角色型存取控制

RBAC 是一種系統，可為在 Azure 中執行的應用程式提供身分識別。 應用程式可以使用此身分識別來存取資源，而不是使用金鑰或密碼。 

## <a name="security-principals"></a>安全性主體

RBAC 中的第一個元件是安全性主體。 安全性主體可以是使用者、群組、服務主體或受控識別。 

![圖10-2 不同類型的安全性主體](./media/rbac-security-principal.png)
**圖 10-2**。 不同類型的安全性主體。

* 使用者-在 Azure Active Directory 中具有帳戶的任何使用者都是使用者。

* 群組-Azure Active Directory 的使用者集合。 身為群組的成員，使用者除了其本身之外，還會接受該群組的角色。

* 服務主體-用來執行服務或應用程式的安全性身分識別。

* 受控識別-由 Azure 管理的 Azure Active Directory 身分識別。 受控識別通常會在開發雲端應用程式時使用，以管理用來向 Azure 服務進行驗證的認證。

安全性主體可以套用至大部分的資源。 這表示您可以將安全性主體指派給在 Azure Kubernetes 內執行的容器，讓它能夠存取儲存在 Key Vault 中的秘密。 Azure 函式可以採取許可權，讓它與 Active Directory 實例交談，以驗證呼叫使用者的 JWT。 一旦使用服務主體啟用服務，就可以使用角色和範圍，以細微的方式管理其許可權。  

## <a name="roles"></a>角色

安全性主體可能會採用許多角色，或使用更 sartorial 的比喻，而磨損許多職。 每個角色都會定義一系列的許可權，例如「從 Azure 服務匯流排端點讀取訊息」。 安全性主體的有效許可權集合是指派給安全性主體所擁有之所有角色的擁有權限組合。 Azure 有大量的內建角色，使用者可以定義自己的角色。

![圖 10-3 RBAC 角色定義](./media/rbac-role-definition.png)
**圖 10-3**。 RBAC 角色定義。

內建在 Azure 中，也有許多高階角色，例如擁有者、參與者、讀者和使用者帳戶管理員。 使用擁有者角色時，安全性主體可以存取所有資源，並將許可權指派給其他人。 參與者具有與所有資源相同的存取層級，但無法指派許可權。 讀者只能查看現有的 Azure 資源，而使用者帳戶系統管理員可以管理對 Azure 資源的存取。

較細微的內建角色（例如[DNS 區域參與者](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#dns-zone-contributor)）具有僅限單一服務的許可權。 安全性主體可以接受任意數目的角色。

## <a name="scopes"></a>範圍

角色可以套用至 Azure 內受限制的一組資源。 例如，將範圍套用至先前從服務匯流排佇列讀取的範例，您可以將許可權縮小為單一佇列：「讀取來自 Azure 服務匯流排端點`blah.servicebus.windows.net/queue1`的訊息」

範圍可以縮小為單一資源，也可以套用至整個資源群組、訂用帳戶，甚至是管理群組。

測試安全性主體是否具有特定許可權時，會將角色和範圍的組合納入考慮。 這種組合提供強大的授權機制。

## <a name="deny"></a>拒絕

先前，RBAC 只允許「允許」規則。 這種行為會使某些範圍變得複雜，而無法建立。 例如，允許所有儲存體帳戶的安全性主體存取權，但其中一個需要授與明確許可權給可能無止盡的儲存體帳戶清單。 每次建立新的儲存體帳戶時，都必須將其新增至此帳戶清單。 這會增加不需要的管理額外負荷。

拒絕規則的優先順序高於允許規則。 現在表示相同的「全部允許但一個」範圍，可以表示為兩個規則：「全部允許」和「拒絕此特定一項」。 拒絕規則不僅易於管理，還允許拒絕所有人的存取，以提供更安全的資源。

## <a name="checking-access"></a>檢查存取權

您可以想像，擁有大量的角色和範圍，可以讓您瞭解服務主體的有效許可權非常困難。 堆積拒絕規則的基礎，只是為了增加複雜性。 幸運的是，有一個許可權計算機可以顯示任何服務主體的有效許可權。 通常會在入口網站的 [IAM] 索引標籤下找到，如圖10-3 所示。

![圖 10-4 app service](./media/check-rbac.png)
的許可權計算機**圖 10-4**。 App service 的許可權計算機。

## <a name="securing-secrets"></a>保護秘密

密碼和憑證是攻擊者常見的攻擊媒介。 密碼破解硬體可以執行暴力密碼破解攻擊，並試著每秒猜測數十億個密碼。 因此，用來存取資源的密碼是強式的，而且有很多不同的字元。 這些密碼就是幾乎不可能記住的密碼類型。 幸運的是，Azure 中的密碼實際上不需要由任何人知道。 

許多安全性[專家會建議](https://www.troyhunt.com/password-managers-dont-have-to-be-perfect-they-just-have-to-be-better-than-not-having-one/)使用密碼管理員來保留您自己的密碼，是最佳的方法。 雖然它會將您的密碼集中在一個位置，但它也允許使用高度複雜的密碼，並確保它們對每個帳戶都是唯一的。 Azure 中存在相同的系統：秘密的集中存放區。

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault 提供集中的位置來儲存資料庫、API 金鑰和憑證等專案的密碼。 一旦將秘密輸入保存庫之後，就不會再次顯示它，而且解壓縮和查看的命令會特意複雜。 Safe 中的資訊會使用軟體加密或 FIPS 140-2 Level 2 驗證的硬體安全性模組來保護。 

金鑰保存庫的存取權是透過 Rbac 提供，這表示不只有任何使用者都可以存取保存庫中的資訊。 假設 web 應用程式希望存取儲存在 Azure Key Vault 中的資料庫連接字串。 若要取得存取權，應用程式必須使用服務主體來執行。 在此假設角色下，他們可以從 safe 讀取秘密。 有一些不同的安全性設定可進一步限制應用程式對保存庫的存取權，使其無法更新秘密，但只能讀取它們。 

可以監視金鑰保存庫的存取權，以確保只有預期的應用程式會存取保存庫。 記錄可以整合回 Azure 監視器，並在發生未預期的狀況時，解除鎖定設定警示的功能。 

## <a name="kubernetes"></a>Kubernetes

在 Kubernetes 中，有一項類似的服務可維護少量的秘密資訊。 Kubernetes 秘密可以透過一般`kubectl`可執行檔來設定。

建立秘密就像尋找要儲存之值的 base64 版本一樣簡單：

```console
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

然後將它新增至名`secret.yml`為的秘密檔案，例如，如下列範例所示：

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

然後，這些秘密可以掛接到磁片區，或透過環境變數公開給容器進程。 建立應用程式的[12 因素應用](https://12factor.net/)程式方法建議使用最低的一般分母，將設定傳輸至應用程式。 環境變數是最低的公分母，因為不論作業系統或應用程式為何都可支援。

使用內建 Kubernetes 秘密的替代方法，是從 Kubernetes 中存取 Azure Key Vault 中的秘密。 若要這麼做，最簡單的方法是將 RBAC 角色指派給想要載入秘密的容器。 然後，應用程式可以使用 Azure Key Vault Api 來存取秘密。 不過，這種方法需要修改程式碼，而且不會遵循使用環境變數的模式。 相反地，您可以透過使用[Azure Key Vault Injector](https://mrdevops.io/introducing-azure-key-vault-to-kubernetes-931f82364354)，將值插入容器中。 這種方法實際上比直接使用 Kubernetes 秘密更安全，因為叢集上的使用者可以存取它們。

## <a name="encryption-in-transit-and-at-rest"></a>傳輸中和待用加密

無論是在磁片上，還是在各種不同的服務之間傳輸，都必須確保資料的安全。 避免資料流程失的最有效方式，是將它加密成不容易被其他人讀取的格式。 Azure 支援各種不同的加密選項。

### <a name="in-transit"></a>傳輸中

有數種方式可加密 Azure 網路上的流量。 Azure 服務的存取權通常是透過使用傳輸層安全性（TLS）的連線來完成。 例如，所有與 Azure Api 的連線都需要 TLS 連線。 同樣地，您可以限制 Azure 儲存體中的端點連線只能透過 TLS 加密連線來使用。

TLS 是一個複雜的通訊協定，而且只知道連線使用 TLS 並不足以確保安全性。 比方說，TLS 1.0 是若長期偏不安全的，TLS 1.1 也不是那麼好。 即使在 TLS 版本內，還有各種不同的設定，可讓連接更容易解密。 最佳做法是檢查並查看伺服器連接是否使用最新且設定完善的通訊協定。 

這項檢查可以透過外部服務來完成，例如 SSL 實驗室的 SSL 伺服器測試。 針對一般 Azure 端點的測試回合（在此案例中為服務匯流排端點），會產生近乎完美的分數。

即使是 Azure SQL 資料庫等服務，也會使用 TLS 加密來防止資料隱藏。 使用 TLS 對傳輸中的資料進行加密的有趣部分是，即使是 Microsoft，也無法在執行 TLS 的電腦之間接聽連接。 這對於擔心其資料可能會有比標準攻擊者更多資源的 Microsoft 適當或甚至是狀態動作專案的公司而言，是非常舒適的。 

![圖 10-5 SSL 實驗室報表顯示服務匯流排端點的分數。**圖 10-5**。 ](./media/ssl-report.png)
 SSL 實驗室報表，顯示服務匯流排端點的分數。

雖然此層級的加密不會對所有時間都足夠，但它應該會激發 Azure TLS 連線相當安全的信心。 Azure 會在加密改善時繼續發展其安全性標準。 瞭解安全性標準和更新 Azure 的情況，是很好的方式。

### <a name="at-rest"></a>待用

在任何應用程式中，資料會放在磁片上的幾個地方。 應用程式程式碼本身是從某種儲存機制載入。 大部分的應用程式也會使用某種類型的資料庫，例如 SQL Server、Cosmos DB，或甚至是出乎意料的價格有效率表格儲存體。 這些資料庫全都使用大量加密的儲存體，以確保具有適當許可權的應用程式以外的任何人都可以讀取您的資料。 即使系統操作員也無法讀取已加密的資料。 因此，客戶可以確保其秘密資訊保持機密。

### <a name="storage"></a>存放裝置

許多 Azure 的基礎都是 Azure 儲存體引擎。 虛擬機器磁片會裝載在 Azure 儲存體上。 Azure Kubernetes Services 會在 Azure 儲存體上裝載的虛擬機器上執行。 即使是無伺服器技術（例如 Azure Functions 應用程式和 Azure 容器實例），也會用盡屬於 Azure 儲存體一部分的磁片。

如果 Azure 儲存體已妥善加密，則它會提供其他所有專案的基礎，也會進行加密。 Azure 儲存體[是](https://docs.microsoft.com/azure/storage/common/storage-service-encryption)使用[FIPS 140-2](https://en.wikipedia.org/wiki/FIPS_140)相容的[256 位 AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)進行加密。 這是一項知名的加密技術，在過去20年或多年來廣泛的學術審查。 目前並沒有任何已知的實際攻擊，讓某人不知道金鑰就能讀取 AES 所加密的資料。

根據預設，用來加密 Azure 儲存體的金鑰是由 Microsoft 所管理。 有廣泛的保護措施，以確保能夠防止惡意存取這些金鑰。 不過，具有特定加密需求的使用者也可以[提供自己的儲存體金鑰](https://docs.microsoft.com/azure/storage/common/storage-encryption-keys-powershell)，並在 Azure Key Vault 中進行管理。 這些金鑰可以隨時撤銷，這會使用無法存取的方式，有效地轉譯儲存體帳戶的內容。

虛擬機器使用加密的儲存體，但您可以使用 Windows 上的 BitLocker 或 Linux 上的 DM Crypt，來提供另一層的加密。 這些技術的意思是，即使磁片映射從存放裝置流失，它還是不可能讀取它。

### <a name="azure-sql"></a>Azure SQL

裝載在 Azure SQL 上的資料庫使用稱為[透明資料加密（TDE）](/sql/relational-databases/security/encryption/transparent-data-encryption)的技術，以確保資料保持加密。 預設會在所有新建立的 SQL 資料庫上啟用此功能，但必須針對舊版資料庫手動啟用。 TDE 不僅會執行資料庫的即時加密和解密，還會執行備份和交易記錄。

加密參數會儲存在`master`資料庫中，而且在啟動時，會將其餘作業讀入記憶體中。 這表示`master`資料庫必須保持未加密狀態。 實際的金鑰是由 Microsoft 管理。 不過，具有嚴格安全性需求的使用者可能會在 Key Vault 中提供自己的金鑰，與 Azure 儲存體的方式大致相同。 Key Vault 提供這類服務的金鑰輪替和撤銷。

TDS 的「透明」部分來自于不需要用戶端變更即可使用加密資料庫的事實。 雖然這種方法可提供良好的安全性，但洩漏資料庫密碼就足以讓使用者能夠解密資料。 還有另一種方法可加密資料庫中的個別資料行或資料表。 [Always Encrypted](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault)可確保在沒有時間點，加密的資料會以純文字顯示在資料庫內。

設定此加密層需要在 SQL Server Management Studio 中透過 wizard 執行，以選取加密的類型，以及在 Key Vault 儲存相關聯金鑰的位置。 

![圖10-6 使用 Always Encrypted](./media/always-encrypted.png)
**圖 10-6**選取要加密之資料表中的資料行。 選取要使用 Always Encrypted 加密之資料表中的資料行。

從這些加密資料行讀取資訊的用戶端應用程式必須進行特殊的額度，才能讀取加密的資料。 連接字串需要使用`Column Encryption Setting=Enabled`進行更新，而且必須從 Key Vault 抓取用戶端認證。 接著，必須使用資料行加密金鑰來可能遭受 SQL Server 用戶端。 完成後，其餘的動作會使用 SQL 用戶端的標準介面。 也就是說，以 SQL 用戶端為基礎的 Dapper 和 Entity Framework 之類的工具，在沒有變更的情況下仍可繼續工作。 每一種語言都可能尚未提供每個 SQL Server 驅動程式的 Always Encrypted。

TDE 和 Always Encrypted 的組合，這兩者都可以與用戶端特定的金鑰搭配使用，以確保甚至支援最嚴格的加密需求。

### <a name="cosmos-db"></a>Cosmos DB

Cosmos DB 是 Microsoft 在 Azure 中提供的最新資料庫。 它是從頭開始建立的，並記住安全性和密碼編譯。 AES-256 位加密對於所有 Cosmos DB 資料庫而言都是標準的，而且無法停用。 結合 TLS 1.2 的通訊需求時，整個儲存體解決方案都會加密。

![圖 10-7 Cosmos DB](./media/cosmos-encryption.png)
**圖 10-7**內的資料加密流程。 Cosmos DB 內的資料加密流程。

雖然 Cosmos DB 並不提供提供客戶加密金鑰的能力，但小組也已經完成許多工作，以確保它維持符合 PCI DSS 的規範。 Cosmos DB 也不支援任何類似 Azure SQL Always Encrypted 的單一資料行加密。

## <a name="keeping-secure"></a>保持安全

Azure 擁有發行高度安全產品所需的所有工具。 不過，連鎖的鏈只會與最弱的連結一樣強。 如果部署在 Azure 之上的應用程式不是以適當的安全性思維和良好的安全性審核來開發，則它們會變成鏈中的弱式連結。 有許多絕佳的靜態分析工具、加密程式庫和安全性作法，可以用來確保安裝在 Azure 上的軟體與 Azure 本身一樣安全。 WhiteSource（[靜態分析工具](https://www.whitesourcesoftware.com/)、[加密程式庫](https://www.libressl.org/)和[安全性作法](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)、LibreSSL （ https://www.libressl.org/) 以及[紅色與Blue-Microsoft Azure](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)的內部安全性滲透測試，分別是其中的範例。 

>[!div class="step-by-step"]
>[上一頁](security.md)
>[下一頁](devops.md) <!-- Next Chapter -->
