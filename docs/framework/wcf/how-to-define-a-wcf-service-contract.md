---
title: 教學課程：定義 Windows Communication Foundation 服務合約
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: a1908339460191fcb81d03d45c56dd57b2cf4c4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228389"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>教學課程：定義 Windows Communication Foundation 服務合約

本教學課程說明建立基本的 Windows Communication Foundation (WCF) 應用程式所需的五個工作中的第一個。 如需教學課程的概觀，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。

當您建立 WCF 服務時，您的第一個工作是定義服務合約。 服務合約會指定服務所支援的作業。 作業可以視為一種 Web 服務方法。 您建立服務合約定義視覺效果C#或 Visual Basic (VB) 介面。 介面具有下列特性：

- 介面中的每一個方法都會對應到一個特定的服務作業。 
- 對於每個介面，您必須套用<xref:System.ServiceModel.ServiceContractAttribute>屬性。
- 對於每個作業/方法，您必須套用<xref:System.ServiceModel.OperationContractAttribute>屬性。 

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 建立**WCF 服務程式庫**專案。
> - 定義服務合約介面。

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>建立 WCF 服務程式庫專案，並定義服務合約介面

1. 以系統管理員身分開啟 Visual Studio。 若要這樣做，請選取 [Visual Studio 方案中的**開始**] 功能表，然後選取**詳細** > **系統管理員身分執行**從捷徑功能表。

2. 建立**WCF 服務程式庫**專案。

   1. 從 [檔案] 功能表選取 [新增] > [專案]。

   2. 在**新的專案** 對話方塊的左側，展開**Visual C#** 或**Visual Basic**，然後選取**WCF**類別目錄。 Visual Studio 視窗的中間區段中顯示專案範本的清單。 選取  **WCF 服務程式庫**。

      > [!NOTE]
      > 如果您沒有看到**WCF**專案範本類別，您可能需要安裝**Windows Communication Foundation** Visual Studio 的元件。 在 **新的專案**對話方塊中，選取**開啟 Visual Studio 安裝程式**左側的連結。 選取 **個別元件**索引標籤，然後尋找並選取**Windows Communication Foundation**之下**開發活動**類別目錄。 選擇**修改**開始安裝元件。

   3. 在視窗的底部區段中，輸入*GettingStartedLib* for**名稱**並*GettingStarted*如**方案名稱**。 

   4. 選取 [確定]。

      Visual Studio 會建立專案，其中有三個檔案：*將 IService1.cs* (或*IService1.vb* Visual Basic 專案)， *Service1.cs* (或*Service1.vb* Visual Basic 專案)，和*App.config*。Visual Studio 會定義這些檔案，如下所示： 
      - *IService1*檔案包含服務合約的預設定義。 
      - *Service1*檔案包含服務合約的預設實作。 
      - *App.config*檔案包含載入預設服務與 Visual Studio WCF 服務主機工具所需的組態資訊。 如需 WCF 服務主機工具的詳細資訊，請參閱[WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)。

      > [!NOTE]
      > 如果您安裝 Visual Studio 與 Visual Basic 開發人員環境設定時，可能會隱藏方案。 如果發生這種情況，請選取**選項**從**工具**功能表，然後選取**專案和方案** > **一般**中**選項**視窗。 選取 **一律顯示方案**。 此外，確認**儲存新專案時建立**已選取。

3. 從**方案總管**，開啟**IService1.cs**或是**IService1.vb**檔案，並以下列程式碼取代其程式碼：

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

     本合約定義了線上計算機。 請注意`ICalculator`介面會標示<xref:System.ServiceModel.ServiceContractAttribute>屬性 (為簡化`ServiceContract`)。 此屬性定義命名空間，以釐清合約名稱。 程式碼將標記與每個計算機作業<xref:System.ServiceModel.OperationContractAttribute>屬性 (為簡化`OperationContract`)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 建立 WCF 服務程式庫專案。
> - 定義服務合約介面。

請前進到下一個教學課程，以了解如何實作 WCF 服務合約。

> [!div class="nextstepaction"]
> [教學課程：實作 WCF 服務合約](how-to-implement-a-wcf-contract.md)
