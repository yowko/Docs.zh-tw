---
title: 設定 HTTP 和 HTTPS
description: 瞭解如何設定 HTTP/HTTPS 以允許 WCF 服務和用戶端進行通訊。 使用 Netsh.exe 設定 URL 註冊和防火牆例外。
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: fbff78ff8e2c5c4fa73a56a3fdc15163596aa985
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245137"
---
# <a name="configuring-http-and-https"></a>設定 HTTP 和 HTTPS

WCF 服務與用戶端可以透過 HTTP 和 HTTPS 進行通訊。 HTTP/HTTPS 設定是使用 Internet Information Services (IIS)，或使用命令列工具設定。 在 IIS HTTP 或 HTTPS 之下裝載 WCF 服務時，設定可以在 IIS (使用 inetmgr.exe 工具) 內進行。 如果是自我裝載的 WCF 服務，可以使用命令列工具設定 HTTP 或 HTTPS 設定。

您至少要設定 URL 註冊，並為您的服務將使用的 URL 新增防火牆例外。 您可以使用 Netsh.exe 工具來設定這些設定。

## <a name="configuring-namespace-reservations"></a>設定命名空間保留

命名空間保留區會將一部分 HTTP URL 命名空間的權限指派給特定的使用者群組。 保留區會授予這些使用者建立服務的權限，以接聽那一部分的命名空間。 保留是 URL 前置詞，這表示保留區會涵蓋保留路徑的所有子路徑。 命名空間保留區允許兩種使用萬用字元的方式。 HTTP 伺服器 API 檔描述[包含萬用字元的命名空間宣告之間的解析順序](/windows/desktop/Http/routing-incoming-requests)。

執行中的應用程式可以建立類似的要求來新增命名空間註冊區。 註冊區與保留區會競爭使用命名空間的各個部分。 根據與[萬用字元的命名空間宣告之間的解析](/windows/desktop/Http/routing-incoming-requests)順序所提供的解析順序，保留的優先順序可能高於註冊。 在此情況中，保留區會封鎖執行中的應用程式，使其無法接收要求。

下列範例會使用 Netsh.exe 工具：

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

此命令會為 DOMAIN\user 帳戶的指定 URL 命名空間新增 URL 保留專案。 如需使用 netsh 命令的詳細資訊，請 `netsh http add urlacl /?` 在命令提示字元中輸入，然後按 enter 鍵。

## <a name="configuring-a-firewall-exception"></a>設定防火牆例外狀況

對透過 HTTP 通訊的 WCF 服務進行自我裝載時，您必須將例外狀況加入至防火牆組態中，以允許使用特殊 URL 的傳入連線。

## <a name="configuring-ssl-certificates"></a>設定 SSL 憑證

Secure Sockets Layer (SSL) 通訊協定會在用戶端與伺服器上使用憑證來儲存加密金鑰。 伺服器會在連線期間提供自己的 SSL 憑證，方便用戶端驗證伺服器的身分識別。 伺服器也可以向用戶端要求憑證，以便連線的雙方進行互相驗證。

憑證會依據 IP 位址與連線的連接埠號碼，儲存在集中保管的存放區。 特殊 IP 位址 0.0.0.0 會符合本機電腦的任何 IP 位址。 請注意，憑證存放區不會根據路徑來區分 Url。 包含相同 IP 位址與連接埠號碼組合的服務必須共用憑證，就算每項服務之 URL 中的路徑都不一樣也需這麼做。

如需逐步指示，請參閱[如何：使用 SSL 憑證設定埠](how-to-configure-a-port-with-an-ssl-certificate.md)。

## <a name="configuring-the-ip-listen-list"></a>設定 IP 接聽清單

一旦使用者註冊了 URL，HTTP 伺服器 API 只會繫結至 IP 位址與連接埠。 根據預設，HTTP 伺服器 API 會針對電腦中的所有 IP 位址繫結至其 URL 中的連接埠。 如果未使用 HTTP 伺服器 API 的應用程式先前已系結至該 IP 位址和埠的組合，就會發生衝突。 IP 接聽清單可讓 WCF 服務與針對機器的部分 IP 位址使用埠的應用程式並存。 如果 IP 接聽清單包含任何項目，則 HTTP 伺服器 API 只會繫結至清單所指定的特定 IP 位址。 您需要系統管理員權限才能修改 IP 接聽清單。

使用 netsh 工具來修改 IP 接聽清單，如下列範例所示：

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a>其他設定

使用 <xref:System.ServiceModel.WSDualHttpBinding> 時，用戶端連線會使用與命名空間保留區及 Windows 防火牆相容的預設值。 如果您選擇自訂雙向連線的用戶端基底位址，則您必須同時在用戶端上設定這些 HTTP 設定值以符合新的位址。

HTTP 伺服器 API 有一些無法透過 Httpcfg.exe 取得的 advanced configuration 設定。 這些設定會維護在登錄中，並套用至所有在系統中使用 HTTP 伺服器 API 的應用程式。 如需這些設定的相關資訊，請參閱[Http.sys IIS 的登錄設定](https://support.microsoft.com/help/820129/http-sys-registry-settings-for-windows)。 大部分的使用者都不需要變更這些設定。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.WSDualHttpBinding>
- [如何：使用 SSL 憑證設定連接埠](how-to-configure-a-port-with-an-ssl-certificate.md)
