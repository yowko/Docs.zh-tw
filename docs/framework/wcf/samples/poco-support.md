---
title: "POCO 支援 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# POCO 支援
這個範例會示範對未標記型別的序列化支援，此種型別就是尚未套用序列化屬性的型別，有時亦稱為「單純舊 CLR 物件」\(Plain Old CLR Object，POCO\) 型別。<xref:System.Runtime.Serialization.DataContractSerializer> 會對所有具有預設建構函式 \(Constructor\) 的公用未標記型別推斷資料合約。資料合約可以讓您在服務間來回傳遞結構化資料。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]未標記型別的詳細資訊，請參閱[可序列化的型別](../../../../docs/framework/wcf/feature-details/serializable-types.md)。  
  
 這個範例是以[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎，但是它會使用複數，而不是基本數字類資料型別。除了未使用 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性以外，此範例也與[基本資料合約](../../../../docs/framework/wcf/samples/basic-data-contract.md)範例類似。  
  
 服務是由網際網路資訊服務 \(IIS\) 所裝載，而用戶端是主控台應用程式 \(.exe\)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 `ComplexNumber` 類別是在 `ServiceContract` 中使用。`ComplexNumber` 型別沒有 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 \(Attribute\)，如下列範例程式碼所示。依預設，所有公用屬性 \(Property\) 和欄位都會經過序列化。  
  
```  
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨機器的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示進行。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## 請參閱  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>   
 [可序列化的型別](../../../../docs/framework/wcf/feature-details/serializable-types.md)