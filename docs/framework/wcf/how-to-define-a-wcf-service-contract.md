---
title: HOW TO：定義 Windows Communication Foundation 服務合約
ms.date: 09/14/2018
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 4f85a51c47eb045d1d2f0111cb217199c9acf0d7
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009004"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>HOW TO：定義 Windows Communication Foundation 服務合約

這是建立基本的 Windows Communication Foundation (WCF) 應用程式所需的六項工作中的第一個。 如需這六個工作的概觀，請參閱[使用者入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。

 建立 WCF 服務時，第一項工作是定義服務合約。 服務合約會指定服務所支援的作業。 作業可以視為一種 Web 服務方法。 合約可以透過定義 C++、C# 或 Visual Basic (VB) 介面來建立。 介面中的每一個方法都會對應到一個特定的服務作業。 每一個介面都要有套用一個 <xref:System.ServiceModel.ServiceContractAttribute>，而且每一個作業都必須套用一個 <xref:System.ServiceModel.OperationContractAttribute> 屬性。 如果具有 <xref:System.ServiceModel.ServiceContractAttribute> 屬性之介面中的方法沒有 <xref:System.ServiceModel.OperationContractAttribute> 屬性，服務就不會公開該方法。

 用於這項工作的程式碼將於本程序之後的範例中提供。

## <a name="define-a-service-contract"></a>定義服務合約

1. 系統管理員身分開啟 Visual Studio 中的程式上按一下滑鼠右鍵**開始**功能表，然後選取**詳細** > **系統管理員身分執行**。

2. 建立 WCF 服務程式庫專案。

   1. 從 [檔案] 功能表選取 [新增] > [專案]。

   2. 在**新的專案** 對話方塊的左側，展開**Visual C#** 或**Visual Basic**，然後選取**WCF**類別目錄。 專案範本清單會顯示在對話方塊中間區段。 選取  **WCF 服務程式庫**。

   3. 輸入`GettingStartedLib`中**名稱**文字方塊中並`GettingStarted`中**方案名稱**在對話方塊底部的文字方塊。

   > [!NOTE]
   > 如果您沒有看到**WCF**專案範本類別，您可能需要安裝**Windows Communication Foundation** Visual Studio 的元件。 在 **新的專案**對話方塊方塊中，按一下連結**開啟 Visual Studio 安裝程式**。 選取 **個別元件**索引標籤，然後尋找並選取**Windows Communication Foundation**之下**開發活動**類別目錄。 選擇**修改**開始安裝元件。

   Visual Studio 會建立含有 3 個檔案的專案： IService1.cs （或 IService1.vb） service1.vb （或 Service1.vb） 和 App.config。IService1 檔案包含預設服務合約。 Service1 檔案包含服務合約的預設實作。 App.config 檔案包含載入預設服務與 Visual Studio WCF 服務主機所需的組態。 如需 WCF 服務主機工具的詳細資訊，請參閱[WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)

3. 開啟 IService1.cs 或 IService1.vb 檔案，並刪除命名空間宣告，讓命名空間宣告內的程式碼。 在命名空間宣告中，定義名為 `ICalculator` 的新介面，如下列程式碼所示。

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     本合約定義了線上計算機。 注意 `ICalculator` 介面有標示 <xref:System.ServiceModel.ServiceContractAttribute> 屬性。 這個屬性會定義用來釐清合約名稱的命名空間。 每個計算機作業都會標示 <xref:System.ServiceModel.OperationContractAttribute> 屬性。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [如何： 實作服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [如何：履行服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [快速入門](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [自我裝載](../../../docs/framework/wcf/samples/self-host.md)