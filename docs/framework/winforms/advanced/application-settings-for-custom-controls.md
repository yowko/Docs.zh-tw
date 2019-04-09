---
title: 自訂控制項的應用程式設定
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: b036167c2e1a4dff557d2ef90eaa964710533410
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169737"
---
# <a name="application-settings-for-custom-controls"></a><span data-ttu-id="1f0c4-102">自訂控制項的應用程式設定</span><span class="sxs-lookup"><span data-stu-id="1f0c4-102">Application Settings for Custom Controls</span></span>
<span data-ttu-id="1f0c4-103">您必須完成某些工作，讓您的自訂控制項能夠保存應用程式設定，在第三方應用程式中裝載控制項時。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-103">You must complete certain tasks to give your custom controls the ability to persist application settings when the controls are hosted in third-party applications.</span></span>  
  
 <span data-ttu-id="1f0c4-104">大部分的應用程式設定功能的相關文件會寫入您要建立的獨立應用程式的假設之下。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-104">Most of the documentation about the Application Settings feature is written under the assumption that you are creating a standalone application.</span></span> <span data-ttu-id="1f0c4-105">不過，如果您要建立其他開發人員將裝載的控制項在其應用程式，您需要採取一些額外的步驟，為您的控制項，以保存其設定正確。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-105">However, if you are creating a control that other developers will host in their applications, you need to take a few additional steps for your control to persist its settings properly.</span></span>  
  
## <a name="application-settings-and-custom-controls"></a><span data-ttu-id="1f0c4-106">應用程式設定和自訂控制項</span><span class="sxs-lookup"><span data-stu-id="1f0c4-106">Application Settings and Custom Controls</span></span>  
 <span data-ttu-id="1f0c4-107">您要讓控制項正確保存它的設定，它必須封裝程序，藉由建立其自己專用的應用程式設定包裝函式類別，衍生自<xref:System.Configuration.ApplicationSettingsBase>。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-107">For your control to properly persist its settings, it must encapsulate the process by creating its own dedicated applications settings wrapper class, derived from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="1f0c4-108">此外，主控制項類別必須實作<xref:System.Configuration.IPersistComponentSettings>。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-108">Additionally, the main control class must implement the <xref:System.Configuration.IPersistComponentSettings>.</span></span> <span data-ttu-id="1f0c4-109">這個介面包含數個屬性，以及兩個方法：<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>和<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-109">The interface contains several properties as well as two methods, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> and <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>.</span></span> <span data-ttu-id="1f0c4-110">如果您將控制項加入表單，使用**Windows Form 設計工具**在 Visual Studio 中，會呼叫 Windows Form<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>自動初始化控制項時，您必須呼叫<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>自行在`Dispose`控制項的方法。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-110">If you add your control to a form using the **Windows Forms Designer** in Visual Studio, Windows Forms will call <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automatically when the control is initialized; you must call <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> yourself in the `Dispose` method of your control.</span></span>  
  
 <span data-ttu-id="1f0c4-111">此外，您應該實作下列為了讓應用程式設定的自訂控制項以在 Visual Studio 這類的設計階段環境中正常運作：</span><span class="sxs-lookup"><span data-stu-id="1f0c4-111">In addition, you should implement the following in order for application settings for custom controls to work properly in design-time environments such as Visual Studio:</span></span>  
  
1.  <span data-ttu-id="1f0c4-112">自訂應用程式設定類別的建構函式與<xref:System.ComponentModel.IComponent>做為單一參數。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-112">A custom application settings class with a constructor that takes an <xref:System.ComponentModel.IComponent> as a single parameter.</span></span> <span data-ttu-id="1f0c4-113">您可以使用這個類別來儲存及載入所有的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-113">Use this class to save and load all of your application settings.</span></span> <span data-ttu-id="1f0c4-114">當您建立這個類別的新執行個體時，傳遞您使用建構函式的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-114">When you create a new instance of this class, pass your custom control using the constructor.</span></span>  
  
2.  <span data-ttu-id="1f0c4-115">已建立並放置在表單上，例如在表單的控制項之後，請建立此自訂設定類別<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-115">Create this custom settings class after the control has been created and placed on a form, such as in the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
 <span data-ttu-id="1f0c4-116">如需建立自訂設定類別的指示，請參閱[How to:建立應用程式設定](how-to-create-application-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-116">For instructions on creating a custom settings class, see [How to: Create Application Settings](how-to-create-application-settings.md).</span></span>  
  
## <a name="settings-keys-and-shared-settings"></a><span data-ttu-id="1f0c4-117">設定索引鍵和共用的設定</span><span class="sxs-lookup"><span data-stu-id="1f0c4-117">Settings Keys and Shared Settings</span></span>  
 <span data-ttu-id="1f0c4-118">有些控制項可用於多次相同的格式。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-118">Some controls can be used multiple times within the same form.</span></span> <span data-ttu-id="1f0c4-119">大部分的情況下，您會想要保存其自己的個別設定這些控制項。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-119">Most of the time, you will want these controls to persist their own individual settings.</span></span> <span data-ttu-id="1f0c4-120">具有<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>屬性上的<xref:System.Configuration.IPersistComponentSettings>，您可以提供用來釐清多個版本的表單上控制項的唯一字串。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-120">With the <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> property on <xref:System.Configuration.IPersistComponentSettings>, you can supply a unique string that acts to disambiguate multiple versions of a control on a form.</span></span>  
  
 <span data-ttu-id="1f0c4-121">最簡單的方式來實作<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>是使用<xref:System.Windows.Forms.Control.Name%2A>屬性的控制項<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-121">The simplest way to implement <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> is to use the <xref:System.Windows.Forms.Control.Name%2A> property of the control for the <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>.</span></span> <span data-ttu-id="1f0c4-122">當您載入或儲存控制項的設定時，您將值傳遞<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>入<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>屬性<xref:System.Configuration.ApplicationSettingsBase>類別。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-122">When you load or save the control's settings, you pass the value of <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> on to the <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> property of the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span> <span data-ttu-id="1f0c4-123">當它保存到 XML 的使用者的設定時，應用程式設定就會使用此唯一索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-123">Application Settings uses this unique key when it persists the user's settings to XML.</span></span> <span data-ttu-id="1f0c4-124">下列程式碼範例示範如何`<userSettings>`區段可能會尋找名為自訂控制項的執行個體`CustomControl1`，將儲存的設定及其`Text`屬性。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-124">The following code example shows how a `<userSettings>` section may look for an instance of a custom control named `CustomControl1` that saves a setting for its `Text` property.</span></span>  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 <span data-ttu-id="1f0c4-125">未提供的值之控制項的任何執行個體<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>會共用相同的設定。</span><span class="sxs-lookup"><span data-stu-id="1f0c4-125">Any instances of a control that do not supply a value for <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> will share the same settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f0c4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f0c4-126">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [<span data-ttu-id="1f0c4-127">應用程式設定架構</span><span class="sxs-lookup"><span data-stu-id="1f0c4-127">Application Settings Architecture</span></span>](application-settings-architecture.md)
