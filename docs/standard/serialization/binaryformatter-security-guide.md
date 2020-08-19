---
title: BinaryFormatter 安全性指南
description: 本文說明 BinaryFormatter 類型的固有安全性風險，以及不同序列化程式要使用的建議。
ms.date: 07/11/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: ac01fe78c9577563641a8b06a232ed614ed8520a
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558838"
---
# <a name="binaryformatter-security-guide"></a>BinaryFormatter 安全性指南

本文適用于下列 .NET 部署：

* .NET Framework 所有版本
* .NET Core 2.1-3。1
* .NET 5.0 和更新版本

## <a name="background"></a>背景

> [!WARNING]
> 此 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 類型是危險的， ***不*** 建議用於資料處理。 應用程式應該儘快停止使用 `BinaryFormatter` ，即使它們認為所要處理的資料值得信任。 `BinaryFormatter` 不安全。

本文也適用于下列類型：

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Web.UI.ObjectStateFormatter>

還原序列化弱點是在, 處理要求承載的威脅類別。 針對應用程式成功利用這些弱點的攻擊者，可能會在目標應用程式內造成拒絕服務 (DoS) 、資訊洩漏或遠端程式碼執行。 此風險類別一致地讓 [OWASP 前10個](https://owasp.org/www-project-top-ten/)。 目標包括以 [各種語言](https://owasp.org/www-community/vulnerabilities/Deserialization_of_untrusted_data)撰寫的應用程式，包括 C/c + +、JAVA 和 c #。

在 .NET 中，最大的風險目標是使用類型來還原序列化資料的應用程式 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 。 `BinaryFormatter` 在整個 .NET 生態系統中廣泛使用，因為它的強大功能和易用性。 不過，這個相同的威力讓攻擊者能夠影響目標應用程式內的控制流程。 成功的攻擊可能會導致攻擊者能夠在目標進程的內容中執行程式碼。

更簡單的方式是，假設對承載的呼叫 `BinaryFormatter.Deserialize` 等同于將該承載解讀為獨立可執行檔並加以啟動。

## <a name="binaryformatter-security-vulnerabilities"></a>BinaryFormatter 安全性弱點

> [!WARNING]
> 搭配 `BinaryFormatter.Deserialize` 未受信任的輸入使用時，方法 __絕對__ 不安全。 強烈建議取用者改為考慮使用本文稍後所述的其中一個替代方案。

`BinaryFormatter` 在還原序列化弱點之前實作為充分瞭解的威脅類別。 因此，程式碼不會遵循新式的最佳作法。 `Deserialize`方法可作為攻擊者用來對取用應用程式執行 DoS 攻擊的向量。 這些攻擊可能會導致應用程式沒有回應，或導致非預期的進程終止。 這類的攻擊無法透過 `SerializationBinder` 或任何其他設定交換器來緩和 `BinaryFormatter` 。 .NET 會將此行為視為 ***設計*** ，且不會發出程式碼更新來修改行為。

`BinaryFormatter.Deserialize` 可能很容易受到其他攻擊類別的攻擊，例如資訊洩漏或遠端程式碼執行。 利用自訂之類的功能 <xref:System.Runtime.Serialization.SerializationBinder> 可能無法正確地緩和這些風險。 有一個可能的原因是，.NET 無法實際發佈安全性更新時，會發現新穎弱點。 取用者應該評估其個別案例，並考慮其對這些風險的潛在風險。

我們建議取用 `BinaryFormatter` 者對其應用程式執行個別的風險評估。 消費者必須自行負責判斷是否要使用 `BinaryFormatter` 。 取用者應該有風險來評估使用的安全性、技術、信譽、法律和法規需求 `BinaryFormatter` 。

## <a name="preferred-alternatives"></a>慣用的替代方案

.NET 提供數個可安全處理不受信任資料的內建序列化程式：

* <xref:System.Xml.Serialization.XmlSerializer> 以及 <xref:System.Runtime.Serialization.DataContractSerializer> 將物件圖形序列化為 XML。 請勿混淆 `DataContractSerializer`  <xref:System.Runtime.Serialization.NetDataContractSerializer> 。
* <xref:System.IO.BinaryReader> 和 <xref:System.IO.BinaryWriter> FOR XML 和 JSON。
* 將 <xref:System.Text.Json> 物件圖形序列化為 JSON 的 api。

## <a name="dangerous-alternatives"></a>危險的替代方案

避免下列序列化程式：

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.ObjectStateFormatter>

上述序列化程式全都執行不受限制的多型多型還原序列化，而且也很危險 `BinaryFormatter` 。

## <a name="the-risks-of-assuming-data-to-be-trustworthy"></a>假設資料值得信任的風險

通常，應用程式開發人員可能會認為它們只處理受信任的輸入。 在某些罕見的情況下，安全的輸入案例是 true。 但是，如果承載不需要開發人員就能跨越信任界限，則會比較常見。

__請考慮使用內部部署伺服器__ ，讓員工使用其工作站的桌面用戶端與服務互動。 這種情況可能會被視為「安全」的設定，可 `BinaryFormatter` 接受使用。 不過，此案例提供惡意程式碼的向量，可取得單一員工電腦的存取權，以散佈到整個企業。 惡意程式碼可以利用企業使用 `BinaryFormatter` ，從員工的工作站橫向移至後端伺服器。 然後，它會竊取公司的敏感性資料。 這類資料可能包括交易秘密或客戶資料。

__另外也請考慮使用 `BinaryFormatter` 來保存儲存狀態的應用程式。__ 這可能是一種安全的案例，因為讀取和寫入您自己的硬碟上的資料，代表的是一種小威脅。 不過，在電子郵件或網際網路之間共用檔很常見，大部分的使用者都不會察覺以具風險的行為來開啟這些下載的檔案。

您可以利用這個案例來惡意地產生效果。 如果應用程式是遊戲，共用儲存檔案的使用者在不知情的情況下會有風險。 開發人員本身也可以設為目標。 攻擊者可能會傳送電子郵件給開發人員的技術支援、附加惡意的資料檔案，並要求支援人員加以開啟。 這類攻擊可能會讓攻擊者在企業中據點。

另一種情況是將資料檔案儲存在雲端儲存體中，並自動在使用者的電腦之間同步處理。 能夠取得雲端儲存體帳戶存取權的攻擊者，可能會損害資料檔案。 此資料檔案將會自動同步至使用者的電腦。 使用者下次開啟資料檔案時，會執行攻擊者的承載。 因此，攻擊者可以利用雲端儲存體帳戶入侵來獲得完整的程式碼執行許可權。

__請考慮從桌面安裝模型移至雲端優先模型的應用程式。__ 此案例包括從桌面應用程式或豐富型用戶端模型移至 web 架構模型的應用程式。 針對桌面應用程式所繪製的任何威脅模型，都不一定適用于雲端式服務。 桌面應用程式的威脅模型可能會將指定的威脅解除為「不感興趣，讓用戶端遭受攻擊」。 但在將遠端使用者視為 (用戶端) 攻擊雲端服務本身時，相同的威脅可能會變得有趣。

> [!NOTE]
> 一般而言，序列化的目的是要將物件傳入或移出應用程式。 威脅模型化練習幾乎一律會將這類資料傳輸標示為跨越信任界限。

## <a name="further-resources"></a>進一步資源

* [YSoSerial.Net](https://github.com/pwntester/ysoserial.net) ，以深入瞭解敵人攻擊應用程式的使用方式 `BinaryFormatter` 。
* 還原序列化弱點的一般背景：
  * [OWASP Top 10-A8： 2017-不安全的還原序列化](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A8-Insecure_Deserialization)
  * [CWE-502：未受信任資料的還原序列化](https://cwe.mitre.org/data/definitions/502.html)
