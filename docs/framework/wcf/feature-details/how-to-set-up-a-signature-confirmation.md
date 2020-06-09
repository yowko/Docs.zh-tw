---
title: HOW TO：設定簽章確認
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 9423922753efee7aac32e430f97307c715e43464
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586906"
---
# <a name="how-to-set-up-a-signature-confirmation"></a>HOW TO：設定簽章確認

簽章*確認*是訊息啟動器的機制，可確保收到的回復是為了回應寄件者的原始訊息而產生的。 簽章確認是定義在 WS-Security 1.1 規格中。 如果端點支援 WS-Security 1.0，您就無法使用簽章確認。

下列程序會指定如何使用 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 啟用簽章確認。 您可以搭配 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 使用相同的程序。 此程式是以[如何：使用 SecurityBindingElement 建立自訂](how-to-create-a-custom-binding-using-the-securitybindingelement.md)系結中找到的基本步驟為基礎。

### <a name="to-enable-signature-confirmation-in-code"></a>若要在程式碼中啟用簽章確認

1. 建立 <xref:System.ServiceModel.Channels.BindingElementCollection> 類別的執行個體。

2. 建立類別的實例 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 。

3. 將 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> 設為 `true`。

4. 將安全性項目新增至繫結集合中。

5. 建立自訂系結，如 how [to：使用 SecurityBindingElement 建立自訂](how-to-create-a-custom-binding-using-the-securitybindingelement.md)系結中所指定。

### <a name="to-enable-signature-confirmation-in-configuration"></a>若要在組態中啟用簽章確認

1. 將 `<customBinding>` 項目新增至組態檔的 `<bindings>` 區段中。

2. 新增 `<binding>` 項目，並將名稱屬性設為適當值。

3. 新增適當的編碼項目。 下列範例會新增 `<TextMessageEncoding>` 項目。

4. 新增 `<security>` 子項目並將 `requireSignatureConfirmation` 屬性設定為 `true`。

5. 選擇性。 若要在啟動程式期間啟用簽章確認，請新增子專案， [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 並將 `requireSignatureConfirmation` 屬性設定為 `true` 。

6. 新增適當的傳輸項目。 下列範例會新增 [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) ：

    ```xml
    <bindings>
      <customBinding>
        <binding name="SignatureConfirmationBinding">
          <security requireSignatureConfirmation="true">
            <secureConversationBootstrap requireSignatureConfirmation="true" />
              </security>
           <textMessageEncoding />
             <httpTransport />
        </binding>
      </customBinding>
    </bindings>
    ```

## <a name="example"></a>範例

下列程式碼會建立 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 的執行個體，並將 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> 屬性設定為 `true`。 請注意，這個範例並未使用之前範例中出現的 `<secureConversationBootstrap>` 項目， 但會在使用 Windows (Kerberos 通訊協定) 權杖時示範簽章確認。 在這種情況下，來自服務的所有回應中都會傳回用戶端的簽章，並且經由用戶端確認。

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [HOW TO：使用 SecurityBindingElement 建立自訂繫結](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [HOW TO：為指定的驗證模式建立 SecurityBindingElement](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
