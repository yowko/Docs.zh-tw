---
title: POCO 支援
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: d416f37e0add99fbe3d60982fd2298748ff78556
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259963"
---
# <a name="poco-support"></a>POCO 支援

這個範例會示範對未標記型別的序列化支援，此種型別就是尚未套用序列化屬性的型別，有時亦稱為「簡單的 CLR 物件」(Plain Old CLR Object，POCO) 型別。 <xref:System.Runtime.Serialization.DataContractSerializer>會針對具有無參數的函式的所有未標記類型推斷資料合約。 資料合約可以讓您在服務間來回傳遞結構化資料。 如需未標記之類型的詳細資訊，請參閱可序列化的 [類型](../feature-details/serializable-types.md)。  
  
 這個範例是以 [消費者入門](getting-started-sample.md)為基礎，但使用複數，而不是基本的數數值型別。 它也類似于「 [基本資料合約](basic-data-contract.md) 」範例，不同之處 <xref:System.Runtime.Serialization.DataContractAttribute> 在於 <xref:System.Runtime.Serialization.DataMemberAttribute> 不會使用和屬性。  
  
 服務是由網際網路資訊服務 (IIS) 所裝載，而用戶端是主控台應用程式 (.exe)。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 `ComplexNumber` 類別是在 `ServiceContract` 中使用。 `ComplexNumber` 型別沒有 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute)，如下列範例程式碼所示。 依預設，所有公用屬性 (Property) 和欄位都會經過序列化。  
  
```csharp
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
  
1. 確定您已 [針對 Windows Communication Foundation 範例執行一次性安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦的設定中執行範例，請遵循執行 [Windows Communication Foundation 範例](running-the-samples.md)中的指示。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [可序列化的型別](../feature-details/serializable-types.md)
