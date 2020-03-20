---
title: 教程：定義 Windows 通信基礎服務協定
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184098"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>教程：定義 Windows 通信基礎服務協定

本教程介紹創建基本 Windows 通信基礎 （WCF） 應用程式所需的五項任務中的第一個。 有關教程的概述，請參閱[教程：開始使用 Windows 通信基礎應用程式](getting-started-tutorial.md)。

創建 WCF 服務時，您的第一個任務是定義服務協定。 服務合約會指定服務所支援的作業。 作業可以視為一種 Web 服務方法。 通過定義 C# 或視覺化基本介面來創建服務協定。 介面具有以下特徵：

- 介面中的每個方法會對應一個特定服務作業。
- 對於每個介面，必須應用該<xref:System.ServiceModel.ServiceContractAttribute>屬性。
- 對於每個操作/方法，必須應用該<xref:System.ServiceModel.OperationContractAttribute>屬性。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> - 創建**WCF 服務庫**專案。
> - 定義服務協定介面。

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>創建 WCF 服務庫專案並定義服務協定介面

1. 以系統管理員身分開啟 Visual Studio。 為此，請在 **"開始"** 功能表中選擇 Visual Studio 程式，然後從快顯功能表中選擇 **"以管理員** > **身份運行**"。

2. 創建**WCF 服務庫**專案。

   1. 從 [檔案]**** 功能表選取 [新增]**** > [專案]****。

   2. 在左側的 **"新專案**"對話方塊中，展開**視覺化 C#** 或**視覺化基本**，然後選擇**WCF**類別。 Visual Studio 在視窗的中心部分顯示專案範本的清單。 選擇**WCF 服務庫**。

      > [!NOTE]
      > 如果您沒有看到**WCF**專案範本類別，則可能需要安裝 Visual Studio 的**Windows 通信基礎**元件。 在 **"新專案**"對話方塊中，選擇左側的 **"打開視覺化工作室安裝程式"** 連結。 選擇 **"單個元件**"選項卡，然後在 **"開發活動**"類別下查找並選擇**Windows 通信基礎**。 選擇 **"修改"** 以開始安裝元件。

   3. 在視窗的底部部分，輸入"獲取*入門Lib"***以**獲取**解決方案名稱的名稱**和*入門*。

   4. 選取 [確定]****。

      Visual Studio 創建的專案有三個檔 *：IService1.cs（* 或用於視覺化基礎專案的*IService1.vb）、Service1.cs（* 或 Visual Basic 專案的*Service1.vb）* 和*App.config*。 *Service1.cs*Visual Studio 定義這些檔如下所示：
      - *IService1*檔包含服務協定的預設定義。
      - *Service1*檔包含服務協定的預設實現。
      - *App.config*檔包含使用 Visual Studio WCF 服務主機工具載入預設服務所需的配置資訊。 有關 WCF 服務主機工具的詳細資訊，請參閱[WCF 服務主機 （WcfSvcHost.exe）。](wcf-service-host-wcfsvchost-exe.md)

      > [!NOTE]
      > 如果安裝了具有視覺化基本開發人員環境設置的 Visual Studio，則解決方案可能已隱藏。 如果是這種情況，請從 **"工具"** 功能表中選擇 **"選項**"，然後在 **"選項"** 視窗中選擇"**專案和解決方案** > **常規**"。 選擇 **"始終顯示解決方案**"。 此外，驗證是否選擇了**創建時保存新專案**。

3. 從**解決方案資源管理器**中打開**IService1.cs**或**IService1.vb**檔，並將其代碼替換為以下代碼：

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

     本合約定義了線上計算機。 請注意，`ICalculator`介面用<xref:System.ServiceModel.ServiceContractAttribute>屬性標記（簡化為`ServiceContract`）。 此屬性定義命名空間以消除協定名稱的歧義。 代碼使用<xref:System.ServiceModel.OperationContractAttribute>屬性標記每個計算機操作（簡化為`OperationContract`）。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> - 創建 WCF 服務庫專案。
> - 定義服務協定介面。

進入下一個教程，瞭解如何實現 WCF 服務協定。

> [!div class="nextstepaction"]
> [教程：實現 WCF 服務協定](how-to-implement-a-wcf-contract.md)
