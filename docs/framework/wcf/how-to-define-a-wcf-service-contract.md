---
title: "HOW TO：定義 Windows Communication Foundation 服務合約 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "服務合約 [WCF], 定義"
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
caps.latest.revision: 58
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 58
---
# HOW TO：定義 Windows Communication Foundation 服務合約
這是在建立基本 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式時必須進行的六個工作中的第一個。如需這六個工作的概觀，請參閱[快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。  
  
 建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務時，第一個工作是要定義服務合約。服務合約會指定服務所支援的作業。作業可以視為一種 Web 服務方法。合約可以透過定義 C\+\+、C\# 或 Visual Basic \(VB\) 介面來建立。介面中的每一個方法都會對應到一個特定的服務作業。每個介面都必須套用 <xref:System.ServiceModel.ServiceContractAttribute>，而且每個作業都必須套用 <xref:System.ServiceModel.OperationContractAttribute> 屬性。如果具有 <xref:System.ServiceModel.ServiceContractAttribute> 屬性之介面中的方法沒有 <xref:System.ServiceModel.OperationContractAttribute> 屬性，服務就不會公開該方法。  
  
 用於這項工作的程式碼將於本程序之後的範例中提供。  
  
### 若要定義服務合約  
  
1.  以滑鼠右鍵按一下 \[**開始**\] 功能表中的程式，並選取 \[**以系統管理員身分執行**\]，以系統管理員的身分開啟 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]。  
  
2.  按一下 \[**檔案**\] 功能表並依序選取 \[**新增**\] 和 \[**專案**\]，以建立 WCF 服務程式庫專案。在 \[**新增專案**\] 對話方塊的左側，針對 C\# 專案展開 \[**Visual C\#**\]，或針對 Visual Basic 專案依序展開 \[**其他語言**\] 和 \[**Visual Basic**\]。選取所選語言下方的 \[**WCF**\]，對話方塊中間區段將會顯示專案範本的清單。選取 \[**WCF 服務程式庫**\]，並在 \[**名稱**\] 文字方塊中輸入 `GettingStartedLib`，以及在對話方塊底部的 \[**方案名稱**\] 文字方塊中輸入 `GettingStarted`。  
  
3.  Visual Studio 將會建立包含 3 個檔案的專案：IService1.cs \(或 IService1.vb\)、Service1.cs \(或 Service1.vb\) 和 App.config。IService1 檔案包含預設服務合約。Service1 檔案包含服務合約的預設實作。App.config 檔案包含載入預設服務與 Visual Studio WCF 服務主機所需的組態。如需 WCF 服務主機工具的詳細資訊，請參閱 [WCF 服務主機 \(WcfSvcHost.exe\)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)。  
  
4.  開啟 IService1.cs 或 IService1.vb 檔案，刪除命名空間宣告內的程式碼，僅保留命名空間宣告。在命名空間宣告內定義名為 `ICalculator` 的新介面，如下列程式碼所示。  
  
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
  
     本合約定義了線上計算器。注意 `ICalculator` 介面有 <xref:System.ServiceModel.ServiceContractAttribute> 屬性的標記。這個屬性會定義用來釐清合約名稱的命名空間。每個計算器作業都有<xref:System.ServiceModel.OperationContractAttribute> 屬性的標記。  
  
    > [!NOTE]
    >  使用屬性對介面、成員或類別進行標註時，您可以在屬性名稱中省略 "Attribute" 的部分。因此，<xref:System.ServiceModel.ServiceContractAttribute> 在 C\# 中會變成 `[ServiceContract]`，而在 Visual Basic 中會變成 `<ServiceContract>`。  
  
## 請參閱  
 <xref:System.ServiceModel.ServiceContractAttribute>   
 <xref:System.ServiceModel.OperationContractAttribute>   
 [HOW TO：實作服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)   
 [使用者入門](../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [自我裝載](../../../docs/framework/wcf/samples/self-host.md)