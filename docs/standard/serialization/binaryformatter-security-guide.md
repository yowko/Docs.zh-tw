---
title: BinaryFormatter 安全性指南
description: 本文說明 BinaryFormatter 類型中固有的安全性風險，以及要使用的不同序列化程式的建議。
ms.date: 07/11/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: f6a54b34bbf1e19212fe37aadb448a1722fe9ff0
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86444761"
---
# <a name="binaryformatter-security-guide"></a>BinaryFormatter 安全性指南

本文適用于下列 .NET 部署：

* .NET Framework 所有版本
* .NET Core 2.1-3。1
* .NET 5.0 和更新版本

## <a name="background"></a>背景

> [!WARNING]
> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>類型是危險的，***不***建議用於資料處理。 應用程式應該儘快停止使用 `BinaryFormatter` ，即使他們認為所處理的資料值得信任。 `BinaryFormatter`不安全，無法安全地進行保護。

本文也適用于下列類型：

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Web.UI.ObjectStateFormatter>

還原序列化弱點是, 處理要求承載的威脅類別。 針對應用程式成功運用這些弱點的攻擊者可能會導致拒絕服務（DoS）、資訊洩漏，或在目標應用程式內執行遠端程式碼。 此風險分類會一致地使[OWASP 的前10個](https://owasp.org/www-project-top-ten/)。 目標包括以[各種語言](https://owasp.org/www-community/vulnerabilities/Deserialization_of_untrusted_data)撰寫的應用程式，包括 c/c + +、JAVA 和 c #。

在 .NET 中，最大的風險目標是使用類型來還原序列化資料的應用程式 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 。 `BinaryFormatter`在 .NET 生態系統中廣泛使用，因為它的威力和易用性。 不過，同樣的威力讓攻擊者能夠影響目標應用程式內的控制流程。 成功的攻擊可能會導致攻擊者能夠在目標進程的內容中執行程式碼。

比較簡單的方式是，假設對承載進行呼叫相當於將 `BinaryFormatter.Deserialize` 該承載解讀為獨立可執行檔並啟動它。

## <a name="binaryformatter-security-vulnerabilities"></a>BinaryFormatter 安全性弱點

> [!WARNING]
> 搭配 `BinaryFormatter.Deserialize` 不受信任的輸入使用時，方法__絕對__不安全。 我們強烈建議取用者改為考慮使用本文稍後所述的其中一種替代方案。

`BinaryFormatter`在還原序列化弱點之前已實作為充分瞭解的威脅類別。 因此，程式碼不會遵循現代化的最佳作法。 `Deserialize`方法可以用來作為向量，讓攻擊者對取用應用程式執行 DoS 攻擊。 這些攻擊可能會導致應用程式沒有回應，或造成非預期的進程終止。 使用或任何其他設定參數，就無法減輕這類的攻擊 `SerializationBinder` `BinaryFormatter` 。 .NET 會將此行為視為***設計***，而且不會發出程式碼更新來修改行為。

`BinaryFormatter.Deserialize`可能容易遭受其他攻擊類別，例如資訊洩漏或遠端程式碼執行。 使用自訂之類的功能 <xref:System.Runtime.Serialization.SerializationBinder> 可能不足以適當地緩和這些風險。 有一個可能的原因是探索到 novel 弱點，而 .NET 無法以實際的發佈安全性更新。 取用者應該評估其個別案例，並考慮其對這些風險的潛在風險。

我們建議取用 `BinaryFormatter` 者在其應用程式上執行個別的風險評量。 取用者會自行負責判斷是否要使用 `BinaryFormatter` 。 取用者應該會有風險，以評估使用的安全性、技術、信譽、法律和法規需求 `BinaryFormatter` 。

## <a name="preferred-alternatives"></a>慣用的替代方案

.NET 提供數個內建的序列化程式，可安全地處理不受信任的資料：

* <xref:System.Xml.Serialization.XmlSerializer>和， <xref:System.Runtime.Serialization.DataContractSerializer> 將物件圖形序列化為 XML。 請勿混淆 `DataContractSerializer` <xref:System.Runtime.Serialization.NetDataContractSerializer> 。
* <xref:System.IO.BinaryReader>和 <xref:System.IO.BinaryWriter> 適用于 XML 和 JSON。
* 用 <xref:System.Text.Json> 來將物件圖形序列化為 JSON 的 api。

## <a name="dangerous-alternatives"></a>危險替代方案

避免下列序列化程式：

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.ObjectStateFormatter>

上述的序列化程式全都執行不受限制的多型多型還原序列化，而且很危險， `BinaryFormatter` 就像

## <a name="the-risks-of-assuming-data-to-be-trustworthy"></a>假設資料值得信任的風險

應用程式開發人員通常會認為他們只會處理受信任的輸入。 在某些罕見的情況下，安全輸入案例是正確的。 但更常見的是，裝載不會跨越信任界限，而開發人員也不會實現它。

__假設有一個內部部署伺服器__，員工使用其工作站的桌面用戶端與服務互動。 這種情況可能會 naïvely 為「安全」的設定，讓您 `BinaryFormatter` 可以接受使用。 不過，此案例會針對惡意程式碼提供一個向量，讓您能夠存取單一員工的電腦，以便在整個企業中散佈。 該惡意程式碼可以利用的企業使用， `BinaryFormatter` 從員工的工作站橫向移到後端伺服器。 然後，它可以竊取公司的敏感性資料。 這類資料可能包含營業秘密或客戶資料。

__另請考慮使用 `BinaryFormatter` 來保存儲存狀態的應用程式。__ 這可能一開始似乎是安全的案例，因為在您自己的硬碟上讀取和寫入資料，代表一個小威脅。 不過，跨電子郵件或網際網路共用檔很常見，大部分的使用者都不會覺得將這些下載的檔案開啟為有風險的行為。

此案例可用於惡意的效果。 如果應用程式是遊戲，共用儲存檔案的使用者會在不知情的情況下自行承擔風險。 開發人員也可以做為目標。 攻擊者可能會透過電子郵件傳送開發人員技術支援、附加惡意資料檔，並要求支援人員開啟它。 這類攻擊可能會讓攻擊者成為企業中的據點。

另一種情況是將資料檔案儲存在雲端儲存體中，並在使用者的電腦之間自動同步處理。 能夠取得雲端儲存體帳戶存取權的攻擊者可能會有害資料檔案。 此資料檔案會自動同步處理到使用者的電腦。 下次使用者開啟資料檔案時，就會執行攻擊者的承載。 因此，攻擊者可以利用雲端儲存體帳戶危害來取得完整的程式碼執行許可權。

__請考慮從桌面安裝模型移至雲端優先模型的應用程式。__ 此案例包括從桌面應用程式或豐富型用戶端模型移至 web 架構模型的應用程式。 針對桌面應用程式所繪製的任何威脅模型，都不一定適用于雲端式服務。 桌面應用程式的威脅模型可能會將指定的威脅關閉為「用戶端不感興趣」。 但是，在認為遠端使用者（用戶端）攻擊雲端服務本身時，相同的威脅可能會變得很有趣。

> [!NOTE]
> 一般來說，序列化的目的是要將物件傳入或傳出應用程式。 威脅模型化練習幾乎一律會將這類資料傳輸標示為跨越信任界限。

## <a name="further-resources"></a>進一步資源

* [YSoSerial.Net](https://github.com/pwntester/ysoserial.net)以研究敵人如何攻擊使用的應用程式 `BinaryFormatter` 。
* [威脅模型](/securityengineering/sdl/threatmodeling)化，以取得威脅模型化應用程式和服務的相關資訊。
* 還原序列化弱點的一般背景：
  * [OWASP Top 10-A8： 2017-不安全的還原序列化](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A8-Insecure_Deserialization)
  * [CWE-502：未受信任資料的還原序列化](https://cwe.mitre.org/data/definitions/502.html)
