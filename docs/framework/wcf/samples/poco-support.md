---
title: POCO 支援
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: ab95469afa53bd0b27efc451875d4912db74a45a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="poco-support"></a>POCO 支援
這個範例會示範對未標記型別的序列化支援，此種型別就是尚未套用序列化屬性的型別，有時亦稱為「簡單的 CLR 物件」(Plain Old CLR Object，POCO) 型別。 <xref:System.Runtime.Serialization.DataContractSerializer> 會對所有具有預設建構函式 (Constructor) 的公用未標記型別推斷資料合約。 資料合約可以讓您在服務間來回傳遞結構化資料。 如需未標記型別，請參閱[可序列化型別](../../../../docs/framework/wcf/feature-details/serializable-types.md)。  
  
 這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，但會使用複數，而不是基本數字型別。 它也是類似於[基本資料合約](../../../../docs/framework/wcf/samples/basic-data-contract.md)範例，不同處在於<xref:System.Runtime.Serialization.DataContractAttribute>和<xref:System.Runtime.Serialization.DataMemberAttribute>屬性不會使用。  
  
 服務是由網際網路資訊服務 (IIS) 所裝載，而用戶端是主控台應用程式 (.exe)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 `ComplexNumber` 類別是在 `ServiceContract` 中使用。 `ComplexNumber` 型別沒有 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute)，如下列範例程式碼所示。 依預設，所有公用屬性 (Property) 和欄位都會經過序列化。  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 [可序列化類型](../../../../docs/framework/wcf/feature-details/serializable-types.md)
