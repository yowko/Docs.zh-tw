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
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="e281b-102">將自訂活動屬性繫結至設計工具控制項</span><span class="sxs-lookup"><span data-stu-id="e281b-102">Binding a custom activity property to a designer control</span></span>
<span data-ttu-id="e281b-103">將文字方塊設計工具控制項繫結至活動引數相當簡單。不過，將複雜的設計工具控制項 (例如下拉式方塊) 繫結至活動引數可能會呈現挑戰。</span><span class="sxs-lookup"><span data-stu-id="e281b-103">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="e281b-104">本主題討論如何將活動引數繫結至自訂活動設計工具上的下拉式方塊控制項。</span><span class="sxs-lookup"><span data-stu-id="e281b-104">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>  
  
#### <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="e281b-105">建立下拉式方塊項目轉換器</span><span class="sxs-lookup"><span data-stu-id="e281b-105">Creating the combo box item converter</span></span>  
  
1.  <span data-ttu-id="e281b-106">在 Visual Studio 中建立名為 CustomProperty 的空白新方案。</span><span class="sxs-lookup"><span data-stu-id="e281b-106">Create a new empty solution in Visual Studio called CustomProperty.</span></span>  
  
2.  <span data-ttu-id="e281b-107">建立名為 ComboBoxItemConverter 的新類別。</span><span class="sxs-lookup"><span data-stu-id="e281b-107">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="e281b-108">加入 System.Windows.Data 的參考，並且讓此類別衍生自 <xref:System.Windows.Data.IValueConverter>。</span><span class="sxs-lookup"><span data-stu-id="e281b-108">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="e281b-109">讓 Visual Studio 實作此介面，以便產生 `Convert` 和 `ConvertBack` 的 Stub。</span><span class="sxs-lookup"><span data-stu-id="e281b-109">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>  
  
3.  <span data-ttu-id="e281b-110">將下列程式碼加入至 `Convert` 方法。</span><span class="sxs-lookup"><span data-stu-id="e281b-110">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="e281b-111">這段程式碼會將型別為 <xref:System.Activities.InArgument%601> 的活動 <xref:System.String> 轉換成要置於設計工具中的值。</span><span class="sxs-lookup"><span data-stu-id="e281b-111">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>  
  
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
  
     <span data-ttu-id="e281b-112">您也可以使用 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 代替 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 來建立上述程式碼片段中的運算式。</span><span class="sxs-lookup"><span data-stu-id="e281b-112">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
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
  
4.  <span data-ttu-id="e281b-113">將下列程式碼加入至 `ConvertBack` 方法。</span><span class="sxs-lookup"><span data-stu-id="e281b-113">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="e281b-114">這段程式碼會將傳入的下拉式方塊項目轉換回 <xref:System.Activities.InArgument%601>。</span><span class="sxs-lookup"><span data-stu-id="e281b-114">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     <span data-ttu-id="e281b-115">您也可以使用 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 代替 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 來建立上述程式碼片段中的運算式。</span><span class="sxs-lookup"><span data-stu-id="e281b-115">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="e281b-116">將 ComboBoxItemConverter 加入至活動的自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="e281b-116">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>  
  
1.  <span data-ttu-id="e281b-117">將新的項目加入至專案。</span><span class="sxs-lookup"><span data-stu-id="e281b-117">Add a new item to the project.</span></span> <span data-ttu-id="e281b-118">在 [新增項目] 對話方塊中，選取 [工作流程] 節點，然後選取 [活動設計工具] 當做新項目的型別。</span><span class="sxs-lookup"><span data-stu-id="e281b-118">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="e281b-119">將此項目命名為 CustomPropertyDesigner。</span><span class="sxs-lookup"><span data-stu-id="e281b-119">Name the item CustomPropertyDesigner.</span></span>  
  
2.  <span data-ttu-id="e281b-120">將下拉式方塊加入至新的設計工具。</span><span class="sxs-lookup"><span data-stu-id="e281b-120">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="e281b-121">在 [項目] 屬性中，將一些項目加入至 [內容] 值為「項目 1」和「項目 2」的下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="e281b-121">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>  
  
3.  <span data-ttu-id="e281b-122">修改下拉式方塊的 XAML，以便加入新的項目轉換器當做要用於下拉式方塊的項目轉換器。</span><span class="sxs-lookup"><span data-stu-id="e281b-122">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="e281b-123">此轉換器會加入成為 ActivityDesigner.Resources 區段中的資源，並且在 <xref:System.Windows.Controls.ComboBox> 的 Converter 屬性中指定轉換器。</span><span class="sxs-lookup"><span data-stu-id="e281b-123">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="e281b-124">請注意，此專案的命名空間指定於活動設計工具的 namespaces 屬性中。如果此設計工具要用於不同的專案，就必須變更這個命名空間。</span><span class="sxs-lookup"><span data-stu-id="e281b-124">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>  
  
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
  
4.  <span data-ttu-id="e281b-125">建立型別為 <xref:System.Activities.CodeActivity> 的新項目。</span><span class="sxs-lookup"><span data-stu-id="e281b-125">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="e281b-126">活動 IDE 所建立的預設程式碼將足以說明此範例。</span><span class="sxs-lookup"><span data-stu-id="e281b-126">The default code created by the IDE for the activity will be sufficient for this example.</span></span>  
  
5.  <span data-ttu-id="e281b-127">將下列屬性加入至類別定義：</span><span class="sxs-lookup"><span data-stu-id="e281b-127">Add the following attribute to the class definition:</span></span>  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     <span data-ttu-id="e281b-128">這一行程式碼會將新的設計工具與新的類別產生關聯。</span><span class="sxs-lookup"><span data-stu-id="e281b-128">This line associates the new designer with the new class.</span></span>  
  
 <span data-ttu-id="e281b-129">此時，新活動應該會與設計工具相關聯。</span><span class="sxs-lookup"><span data-stu-id="e281b-129">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="e281b-130">若要測試新活動，請將它加入至工作流程，並將下拉式方塊設定為兩個值。</span><span class="sxs-lookup"><span data-stu-id="e281b-130">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="e281b-131">然後，[屬性] 視窗應該會更新以反映下拉式方塊的值。</span><span class="sxs-lookup"><span data-stu-id="e281b-131">The properties window should update to reflect the combo box value.</span></span>
