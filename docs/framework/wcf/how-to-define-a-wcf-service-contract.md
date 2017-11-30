---
title: "HOW TO：定義 Windows Communication Foundation 服務合約"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
caps.latest.revision: "58"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ffe53d3e44f86feadc292eccb1692bd58a0c056
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>HOW TO：定義 Windows Communication Foundation 服務合約
這是在建立基本 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式時必須進行的六項工作中的第一項。 六個工作的概觀，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。  
  
 建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務時，第一項工作是要定義服務合約。 服務合約會指定服務所支援的作業。 作業可以視為一種 Web 服務方法。 合約可以透過定義 C++、C# 或 Visual Basic (VB) 介面來建立。 介面中的每一個方法都會對應到一個特定的服務作業。 每一個介面都要有套用一個 <xref:System.ServiceModel.ServiceContractAttribute>，而且每一個作業都必須套用一個 <xref:System.ServiceModel.OperationContractAttribute> 屬性。 如果具有 <xref:System.ServiceModel.ServiceContractAttribute> 屬性之介面中的方法沒有 <xref:System.ServiceModel.OperationContractAttribute> 屬性，服務就不會公開該方法。  
  
 用於這項工作的程式碼將於本程序之後的範例中提供。  
  
### <a name="to-define-a-service-contract"></a>若要定義服務合約  
  
1.  開啟[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]身為系統管理員，以滑鼠右鍵按一下中的程式**啟動**功能表，然後選取**系統管理員身分執行**。  
  
2.  建立 WCF 服務程式庫專案，依序按一下**檔案**功能表，然後選取**新增**，**專案**。 在**新專案** 對話方塊中，在對話方塊的左側展開**Visual C#** C# 專案或**其他語言**然後**Visual Basic** Visual Basic 專案。 在 選取的語言下選取**WCF**和專案範本清單將會顯示在對話方塊中間區段。 選取**WCF 服務程式庫**，並輸入`GettingStartedLib`中**名稱**文字方塊和`GettingStarted`中**方案名稱**在對話方塊底部的文字方塊。  
  
3.  Visual Studio 將會建立包含下列 3 個檔案的專案：IService1.cs (或 IService1.vb)、Service1.cs (或 Service1.vb) 和 App.config。IService1 檔案包含預設服務合約。  Service1 檔案包含服務合約的預設實作。 App.config 檔案包含載入預設服務與 Visual Studio WCF 服務主機所需的組態。 如需 WCF 服務主機工具的詳細資訊，請參閱[WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
4.  開啟 IService1.cs 或 IService1.vb 檔案，刪除命名空間宣告內的程式碼，僅保留命名空間宣告。 在命名空間宣告中，定義名為 `ICalculator` 的新介面，如下列程式碼所示。  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
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
  
    ```  
    ‘IService.vb  
    Imports System  
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
  
    > [!NOTE]
    >  使用屬性來標註介面、成員或類別時，您可以在屬性名稱中省略 "Attribute" 的部分。 因此，<xref:System.ServiceModel.ServiceContractAttribute> 在 C# 中會變成 `[ServiceContract]`，而在 Visual Basic 中會變成 `<ServiceContract>`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [如何：履行服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [快速入門](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自我裝載](../../../docs/framework/wcf/samples/self-host.md)
