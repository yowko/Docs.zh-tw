---
title: 教學課程：定義 Windows Communication Foundation 服務合約
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: ba88fc6ba4cba8d46ed1b43080d471b1b7c4bd75
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928879"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>教學課程：定義 Windows Communication Foundation 服務合約

本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第一個。 如需教學課程的總覽，請[參閱教學課程：Windows Communication Foundation 應用程式](getting-started-tutorial.md)入門。

當您建立 WCF 服務時，您的第一項工作是定義服務合約。 服務合約會指定服務所支援的作業。 作業可以視為一種 Web 服務方法。 您可以藉由定義視覺效果C#或 VISUAL BASIC （VB）介面來建立服務合約。 介面具有下列特性：

- 介面中的每一個方法都會對應到一個特定的服務作業。 
- 針對每個介面，您必須<xref:System.ServiceModel.ServiceContractAttribute>套用屬性。
- 針對每個作業/方法，您必須<xref:System.ServiceModel.OperationContractAttribute>套用屬性。 

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 建立**WCF 服務程式庫**專案。
> - 定義服務合約介面。

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>建立 WCF 服務程式庫專案和定義服務合約介面

1. 以系統管理員身分開啟 Visual Studio。 若要這麼做，請在 [**開始**] 功能表中選取 [Visual Studio] 程式，然後從快捷方式功能表選取 [**更多** > **以系統管理員身分執行**]。

2. 建立**WCF 服務程式庫**專案。

   1. 從 [檔案] 功能表選取 [新增] > [專案]。

   2. 在 [**新增專案**] 對話方塊左側，展開 [**視覺效果C#**  ] 或 [ **Visual Basic**]，然後選取 [ **WCF** ] 分類。 Visual Studio 會在視窗的中間區段顯示專案範本清單。 選取 [ **WCF 服務程式庫**]。

      > [!NOTE]
      > 如果您沒有看到 [ **WCF**專案範本] 類別目錄，您可能需要安裝 Visual Studio 的**Windows Communication Foundation**元件。 在 [**新增專案**] 對話方塊中，選取左側的 [**開啟 Visual Studio 安裝程式**] 連結。 選取 [**個別元件**] 索引標籤，然後尋找並選取 [**開發活動**] 類別底下的 [ **Windows Communication Foundation** ]。 選擇 [**修改**] 開始安裝元件。

   3. 在視窗的下方區段中，針對 [**名稱**] 輸入*GettingStartedLib* ，然後在 [**方案名稱**] 中輸入*GettingStarted* 。 

   4. 選取 [確定]。

      Visual Studio 會建立專案，其中包含三個檔案：*IService1.cs* （或適用于 Visual Basic 專案的*IService1* ）、 *Service1.cs* （或 Visual Basic 專案的*Service1* ）和*app.config*。Visual Studio 定義這些檔案，如下所示： 
      - *IService1*檔案包含服務合約的預設定義。 
      - *Service1*檔案包含服務合約的預設執行。 
      - *App.config*檔案包含使用 Visual Studio WCF 服務主機工具載入預設服務時所需的設定資訊。 如需 WCF 服務主機工具的詳細資訊，請參閱[Wcf 服務主機（WcfSvcHost .exe）](wcf-service-host-wcfsvchost-exe.md)。

      > [!NOTE]
      > 如果您已使用 Visual Basic 的開發人員環境設定來安裝 Visual Studio，解決方案可能會隱藏起來。 如果是這種情況，請從 [**工具**] 功能表中選取 [**選項**]，然後選取 [**選項**] 視窗中的 [**專案和方案** > ] **[一般**]。 選取 [**永遠顯示方案**]。 此外，請確認已選取 [**建立時儲存新專案**]。

3. 從**方案總管**開啟**IService1.cs**或**IService1**檔案，並將其程式碼取代為下列程式碼：

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

     本合約定義了線上計算機。 請注意`ICalculator` ，介面是<xref:System.ServiceModel.ServiceContractAttribute>以屬性標記（簡化為`ServiceContract`）。 這個屬性會定義命名空間來區分合約名稱。 程式碼會使用<xref:System.ServiceModel.OperationContractAttribute>屬性來標示每個計算機作業（簡化為`OperationContract`）。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 建立 WCF 服務程式庫專案。
> - 定義服務合約介面。

請前進到下一個教學課程，以瞭解如何執行 WCF 服務合約。

> [!div class="nextstepaction"]
> [教學課程：執行 WCF 服務合約](how-to-implement-a-wcf-contract.md)
