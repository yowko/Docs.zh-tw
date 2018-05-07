---
title: 使用自訂類型之切換活動的使用
ms.date: 03/30/2017
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
ms.openlocfilehash: 2b6f3109324064cb5e746de9c61e5a70c4c4d60b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a>使用自訂類型之切換活動的使用
這個範例描述如何啟用 <xref:System.Activities.Statements.Switch%601> 活動，在執行階段評估使用者定義的複雜類型。 在大部分傳統的程序性程式語言，[切換](http://go.microsoft.com/fwlink/?LinkId=180521)陳述式選取根據變數的條件評估的執行邏輯。 傳統上，`switch` 陳述式適用於可靜態評估的運算式。 例如，在 C# 中，這表示僅支援基本型別 (例如 <xref:System.Boolean>、<xref:System.Int32> 和 <xref:System.String>)，以及列舉型別。  
  
 若要在自訂類別上啟用切換，必須實作可在執行階段評估自訂複雜類型值的邏輯。 這個範例示範如何在名為 `Person` 的自訂複雜類型上啟用切換。  
  
-   在自訂類別 `Person` 中，<xref:System.ComponentModel.TypeConverter> 屬性是以自訂 <xref:System.ComponentModel.TypeConverter> 的名稱來宣告。  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   在自訂類別 `Person` 中，會覆寫 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 類別。  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
    ```  
  
-   實作自訂 <xref:System.ComponentModel.TypeConverter> 類別，將自訂類別執行個體轉換成字串，並將字串轉換成自訂類別執行個體。  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 下列檔案包含在此範例中：  
  
-   **Person.cs**： 定義`Person`類別。  
  
-   **PersonConverter.cs**： 的類型轉換器`Person`類別。  
  
-   **Sequence.xaml**： 切換工作流程`Person`型別。  
  
-   **Program.cs**： 執行工作流程的主要功能。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入 Switch.sln。  
  
2.  按下 CTRL+SHIFT+B 以建置方案。  
  
3.  按 CTRL+F5 以執行範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>另請參閱  
 [內建活動程式庫](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
