---
title: 將自訂活動屬性繫結至設計工具控制項
ms.date: 03/30/2017
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
ms.openlocfilehash: 1aa22403f5ed2de6893f8bfec9f03fa7dabd6868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513545"
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a>將自訂活動屬性繫結至設計工具控制項
將文字方塊設計工具控制項繫結至活動引數相當簡單。不過，將複雜的設計工具控制項 (例如下拉式方塊) 繫結至活動引數可能會呈現挑戰。 本主題討論如何將活動引數繫結至自訂活動設計工具上的下拉式方塊控制項。  
  
#### <a name="creating-the-combo-box-item-converter"></a>建立下拉式方塊項目轉換器  
  
1.  在 Visual Studio 中建立名為 CustomProperty 的空白新方案。  
  
2.  建立名為 ComboBoxItemConverter 的新類別。 加入 System.Windows.Data 的參考，並且讓此類別衍生自 <xref:System.Windows.Data.IValueConverter>。 讓 Visual Studio 實作此介面，以便產生 `Convert` 和 `ConvertBack` 的 Stub。  
  
3.  將下列程式碼加入至 `Convert` 方法。 這段程式碼會將型別為 <xref:System.Activities.InArgument%601> 的活動 <xref:System.String> 轉換成要置於設計工具中的值。  
  
    ```  
    ModelItem modelItem = value as ModelItem;  
    if (value != null)  
    {  
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;  
  
        if (inArgument != null)  
        {  
            Activity<string> expression = inArgument.Expression;  
            VisualBasicValue<string> vbexpression = expression as VisualBasicValue<string>;  
            Literal<string> literal = expression as Literal<string>;  
  
            if (literal != null)  
            {  
                return "\"" + literal.Value + "\"";  
            }  
            else if (vbexpression != null)  
            {  
                return vbexpression.ExpressionText;  
            }  
        }  
    }  
    return null;  
    ```  
  
     您也可以使用 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 代替 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 來建立上述程式碼片段中的運算式。  
  
    ```  
    ModelItem modelItem = value as ModelItem;  
    if (value != null)  
    {  
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;  
  
        if (inArgument != null)  
        {  
            Activity<string> expression = inArgument.Expression;  
            CSharpValue<string> csexpression = expression as CSharpValue<string>;  
            Literal<string> literal = expression as Literal<string>;  
  
            if (literal != null)  
            {  
                return "\"" + literal.Value + "\"";  
            }  
            else if (csexpression != null)  
            {  
                return csexpression.ExpressionText;  
            }  
        }  
    }  
    return null;  
    ```  
  
4.  將下列程式碼加入至 `ConvertBack` 方法。 這段程式碼會將傳入的下拉式方塊項目轉換回 <xref:System.Activities.InArgument%601>。  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     您也可以使用 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 代替 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 來建立上述程式碼片段中的運算式。  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a>將 ComboBoxItemConverter 加入至活動的自訂設計工具  
  
1.  將新的項目加入至專案。 在 [新增項目] 對話方塊中，選取 [工作流程] 節點，然後選取 [活動設計工具] 當做新項目的型別。 將此項目命名為 CustomPropertyDesigner。  
  
2.  將下拉式方塊加入至新的設計工具。 在 [項目] 屬性中，將一些項目加入至 [內容] 值為「項目 1」和「項目 2」的下拉式方塊。  
  
3.  修改下拉式方塊的 XAML，以便加入新的項目轉換器當做要用於下拉式方塊的項目轉換器。 此轉換器會加入成為 ActivityDesigner.Resources 區段中的資源，並且在 <xref:System.Windows.Controls.ComboBox> 的 Converter 屬性中指定轉換器。 請注意，此專案的命名空間指定於活動設計工具的 namespaces 屬性中。如果此設計工具要用於不同的專案，就必須變更這個命名空間。  
  
    ```  
    <sap:ActivityDesigner x:Class="CustomProperty.CustomPropertyDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:c="clr-namespace:CustomProperty"  
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
  
        <sap:ActivityDesigner.Resources>  
            <ResourceDictionary>  
                <c:ComboBoxItemConverter x:Key="comboBoxItemConverter"/>  
            </ResourceDictionary>  
        </sap:ActivityDesigner.Resources>  
        <Grid>  
            <ComboBox SelectedValue="{Binding Path=ModelItem.Text, Mode=TwoWay, Converter={StaticResource comboBoxItemConverter}}"  Height="23" HorizontalAlignment="Left" Margin="132,5,0,0" Name="comboBox1" VerticalAlignment="Top" Width="120" ItemsSource="{Binding}">  
                <ComboBoxItem>item1</ComboBoxItem>  
                <ComboBoxItem>item2</ComboBoxItem>  
            </ComboBox>  
        </Grid>  
    </sap:ActivityDesigner>  
    ```  
  
4.  建立型別為 <xref:System.Activities.CodeActivity> 的新項目。 活動 IDE 所建立的預設程式碼將足以說明此範例。  
  
5.  將下列屬性加入至類別定義：  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     這一行程式碼會將新的設計工具與新的類別產生關聯。  
  
 此時，新活動應該會與設計工具相關聯。 若要測試新活動，請將它加入至工作流程，並將下拉式方塊設定為兩個值。 然後，[屬性] 視窗應該會更新以反映下拉式方塊的值。
