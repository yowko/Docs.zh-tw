---
title: 如何：使用雙工合約存取服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: bc42792b827b49265a0b1addf959de2fa1a041e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597211"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>如何：使用雙工合約存取服務

Windows Communication Foundation （WCF）的其中一項功能，就是建立使用雙工訊息模式之服務的能力。 這個模式可讓服務透過回呼與用戶端通訊。 本主題說明在執行回呼介面的用戶端類別中建立 WCF 用戶端的步驟。

雙重繫結會向服務公開用戶端的 IP 位址， 用戶端應該利用安全性來確保它只與信任的服務連接。

如需建立基本 WCF 服務和用戶端的教學課程，請參閱[消費者入門教學](../getting-started-tutorial.md)課程。

## <a name="to-access-a-duplex-service"></a>若要存取雙工服務

1. 建立包含兩個介面的服務。 第一個介面主要供服務使用，第二個則是供回呼使用。 如需建立雙工服務的詳細資訊，請參閱[如何：建立雙工合約](how-to-create-a-duplex-contract.md)。

2. 執行服務。

3. 使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端的合約（介面）。 如需如何執行此動作的詳細資訊，請參閱[如何：建立用戶端](../how-to-create-a-wcf-client.md)。

4. 依下列範例所示，在用戶端類別中實作回呼介面。

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. 建立 <xref:System.ServiceModel.InstanceContext> 類別的執行個體。 建構函式需要用戶端類別的執行個體。

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. 使用需要物件的構造函式，建立 WCF 用戶端的實例 <xref:System.ServiceModel.InstanceContext> 。 建構函式的第二個參數就是組態檔中找到的端點名稱。

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. 視需要呼叫 WCF 用戶端的方法。

## <a name="example"></a>範例

下列程式碼範例會示範如何建立會存取雙工合約的用戶端類別。

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a>請參閱

- [消費者入門教學課程](../getting-started-tutorial.md)
- [HOW TO：建立雙工合約](how-to-create-a-duplex-contract.md)
- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [如何：建立用戶端](../how-to-create-a-wcf-client.md)
- [如何：使用 ChannelFactory](how-to-use-the-channelfactory.md)
