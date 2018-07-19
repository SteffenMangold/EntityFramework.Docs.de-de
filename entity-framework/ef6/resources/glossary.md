---
title: Entity Framework-Glossar – EF6
author: divega
ms.date: 2016-10-23
ms.prod: entity-framework
ms.author: divega
ms.manager: avickers
ms.technology: entity-framework-6
ms.topic: article
ms.assetid: 3f05ffdd-49bc-499c-9732-4a368bf5d2d7
caps.latest.revision: 3
ms.openlocfilehash: cbd61838afc23dfb37cee7c624c65476c5270099
ms.sourcegitcommit: bdd06c9a591ba5e6d6a3ec046c80de98f598f3f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2018
ms.locfileid: "39121459"
---
# <a name="entity-framework-glossary"></a><span data-ttu-id="461f5-102">Entity Framework – Glossar</span><span class="sxs-lookup"><span data-stu-id="461f5-102">Entity Framework Glossary</span></span>
## <a name="code-first"></a><span data-ttu-id="461f5-103">Code First</span><span class="sxs-lookup"><span data-stu-id="461f5-103">Code First</span></span>
<span data-ttu-id="461f5-104">Erstellen eines Entity Framework-Datenmodells mithilfe von Code.</span><span class="sxs-lookup"><span data-stu-id="461f5-104">Creating an Entity Framework model using code.</span></span> <span data-ttu-id="461f5-105">Das Modell kann als Ziel und vorhandene oder eine neue Datenbank.</span><span class="sxs-lookup"><span data-stu-id="461f5-105">The model can target and existing database or a new database.</span></span>

## <a name="context"></a><span data-ttu-id="461f5-106">Kontext</span><span class="sxs-lookup"><span data-stu-id="461f5-106">Context</span></span>
<span data-ttu-id="461f5-107">Eine Klasse darstellt, die eine Sitzung mit der Datenbank, sodass Sie Abfragen und Speichern von Daten.</span><span class="sxs-lookup"><span data-stu-id="461f5-107">A class that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="461f5-108">Ein Kontext wird von der "DbContext" bzw. ObjectContext-Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="461f5-108">A context derives from the DbContext or ObjectContext class.</span></span>

## <a name="convention-code-first"></a><span data-ttu-id="461f5-109">Konvention (Code First)</span><span class="sxs-lookup"><span data-stu-id="461f5-109">Convention (Code First)</span></span>
<span data-ttu-id="461f5-110">Eine Regel, die Entity Framework verwendet wird, um die Form des Modells aus Ihren Klassen abzuleiten.</span><span class="sxs-lookup"><span data-stu-id="461f5-110">A rule that Entity Framework uses to infer the shape of you model from your classes.</span></span>

## <a name="database-first"></a><span data-ttu-id="461f5-111">Zunächst-Datenbank</span><span class="sxs-lookup"><span data-stu-id="461f5-111">Database First</span></span>
<span data-ttu-id="461f5-112">Erstellen ein Entity Framework-Datenmodell, das mit dem EF-Designer, die eine vorhandene Datenbank ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="461f5-112">Creating an Entity Framework model, using the EF Designer, that targets an existing database.</span></span>

## <a name="eager-loading"></a><span data-ttu-id="461f5-113">Eager Loading</span><span class="sxs-lookup"><span data-stu-id="461f5-113">Eager loading</span></span>
<span data-ttu-id="461f5-114">Ein Muster laden zugehöriger Daten, in dem eine Abfrage für einen Entitätstyp auch verknüpfte Entitäten als Teil der Abfrage wird geladen.</span><span class="sxs-lookup"><span data-stu-id="461f5-114">A pattern of loading related data where a query for one type of entity also loads related entities as part of the query.</span></span>

## <a name="ef-designer"></a><span data-ttu-id="461f5-115">EF-Designer</span><span class="sxs-lookup"><span data-stu-id="461f5-115">EF Designer</span></span>
<span data-ttu-id="461f5-116">Ein visueller Designer in Visual Studio, die Sie erstellen ein Entity Framework-Datenmodell, das mithilfe der Felder und Linien können.</span><span class="sxs-lookup"><span data-stu-id="461f5-116">A visual designer in Visual Studio that allows you to create an Entity Framework model using boxes and lines.</span></span>

## <a name="entity"></a><span data-ttu-id="461f5-117">Entität</span><span class="sxs-lookup"><span data-stu-id="461f5-117">Entity</span></span>
<span data-ttu-id="461f5-118">Eine Klasse oder ein Objekt, die oder das Anwendungsdaten darstellt, z. B. Kunden, Bestellungen und Produkte.</span><span class="sxs-lookup"><span data-stu-id="461f5-118">A class or object that represents application data such as customers, products, and orders.</span></span>

## <a name="entity-data-model"></a><span data-ttu-id="461f5-119">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="461f5-119">Entity Data Model</span></span>
<span data-ttu-id="461f5-120">Ein Modell, das Entitäten und die Beziehungen zwischen ihnen beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="461f5-120">A model that describes entities and the relationships between them.</span></span> <span data-ttu-id="461f5-121">EF verwendet EDM, um das konzeptionelle Modell für das Beschreiben der Developer-Programmen.</span><span class="sxs-lookup"><span data-stu-id="461f5-121">EF uses EDM to describe the conceptual model against which the developer programs.</span></span> <span data-ttu-id="461f5-122">EDM baut auf dem Entitätsbeziehungsmodell von Dr. eingeführt. Peter Chen.</span><span class="sxs-lookup"><span data-stu-id="461f5-122">EDM builds on the Entity Relationship model introduced by Dr. Peter Chen.</span></span> <span data-ttu-id="461f5-123">Das EDM wurde ursprünglich mit der primäre Zweck von zu common Data Model für eine Suite von Entwickler- und servertechnologien von Microsoft entwickelt.</span><span class="sxs-lookup"><span data-stu-id="461f5-123">The EDM was originally developed with the primary goal of becoming the common data model across a suite of developer and server technologies from Microsoft.</span></span> <span data-ttu-id="461f5-124">EDM wird auch als Teil des OData-Protokolls verwendet.</span><span class="sxs-lookup"><span data-stu-id="461f5-124">EDM is also used as part of the OData protocol.</span></span>

## <a name="explicit-loading"></a><span data-ttu-id="461f5-125">Explizites Laden</span><span class="sxs-lookup"><span data-stu-id="461f5-125">Explicit loading</span></span>
<span data-ttu-id="461f5-126">Ein Muster laden zugehöriger Daten, in dem verbundene Objekte geladen werden, indem Sie eine API aufruft.</span><span class="sxs-lookup"><span data-stu-id="461f5-126">A pattern of loading related data where related objects are loaded by calling an API.</span></span>

## <a name="fluent-api"></a><span data-ttu-id="461f5-127">Fluent-API</span><span class="sxs-lookup"><span data-stu-id="461f5-127">Fluent API</span></span>
<span data-ttu-id="461f5-128">Eine API, die zum Konfigurieren eines Code First-Modells verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="461f5-128">An API that can be used to configure a Code First model.</span></span>

## <a name="foreign-key-association"></a><span data-ttu-id="461f5-129">Fremdschlüsselzuordnung</span><span class="sxs-lookup"><span data-stu-id="461f5-129">Foreign key association</span></span>
<span data-ttu-id="461f5-130">Eine Zuordnung zwischen Entitäten, in denen eine Eigenschaft, die den Fremdschlüssel darstellt, in der Klasse der abhängigen Entität enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="461f5-130">An association between entities where a property that represents the foreign key is included in the class of the dependent entity.</span></span> <span data-ttu-id="461f5-131">Produkt enthält z. B. eine CategoryId-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="461f5-131">For example, Product contains a CategoryId property.</span></span>

## <a name="identifying-relationship"></a><span data-ttu-id="461f5-132">Identifizierende Beziehung</span><span class="sxs-lookup"><span data-stu-id="461f5-132">Identifying relationship</span></span>
<span data-ttu-id="461f5-133">Eine Beziehung, in der der Primärschlüssel der Prinzipalentität Teil des Primärschlüssels der abhängigen Entität ist.</span><span class="sxs-lookup"><span data-stu-id="461f5-133">A relationship where the primary key of the principal entity is part of the primary key of the dependent entity.</span></span> <span data-ttu-id="461f5-134">Bei diesem Beziehungstyp kann die abhängige Entität nicht ohne die Prinzipalentität vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="461f5-134">In this kind of relationship, the dependent entity cannot exist without the principal entity.</span></span>

## <a name="independent-association"></a><span data-ttu-id="461f5-135">Unabhängige Zuordnung</span><span class="sxs-lookup"><span data-stu-id="461f5-135">Independent association</span></span>
<span data-ttu-id="461f5-136">Eine Zuordnung zwischen Entitäten, es keine Eigenschaft gibt, die den Fremdschlüssel in der Klasse der abhängigen Entität darstellt.</span><span class="sxs-lookup"><span data-stu-id="461f5-136">An association between entities where there is no property representing the foreign key in the class of the dependent entity.</span></span> <span data-ttu-id="461f5-137">Beispielsweise enthält eine Product-Klasse eine Beziehung zur aber keine CategoryId-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="461f5-137">For example, a Product class contains a relationship to Category but no CategoryId property.</span></span> <span data-ttu-id="461f5-138">Entitätsframework verfolgt den Status der Zuordnung unabhängig von den Zustand der Entitäten an die beiden Zuordnungsenden.</span><span class="sxs-lookup"><span data-stu-id="461f5-138">Entity Framework tracks the state of the association independently of the state of the entities at the two association ends.</span></span>

## <a name="lazy-loading"></a><span data-ttu-id="461f5-139">Lazy Loading</span><span class="sxs-lookup"><span data-stu-id="461f5-139">Lazy loading</span></span>
<span data-ttu-id="461f5-140">Ein Muster zum Laden von verknüpften Daten, in denen verknüpfte Objekte automatisch geladen werden, wenn eine Navigationseigenschaft zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="461f5-140">A pattern of loading related data where related objects are automatically loaded when a navigation property is accessed.</span></span>

## <a name="model-first"></a><span data-ttu-id="461f5-141">Model First</span><span class="sxs-lookup"><span data-stu-id="461f5-141">Model First</span></span>
<span data-ttu-id="461f5-142">Erstellen ein Entity Framework-Datenmodell, das mit dem EF-Designer wird, klicken Sie dann zum Erstellen einer neuen Datenbank.</span><span class="sxs-lookup"><span data-stu-id="461f5-142">Creating an Entity Framework model, using the EF Designer, that is then used to create a new database.</span></span>

## <a name="navigation-property"></a><span data-ttu-id="461f5-143">Navigationseigenschaft</span><span class="sxs-lookup"><span data-stu-id="461f5-143">Navigation property</span></span>
<span data-ttu-id="461f5-144">Eine Eigenschaft einer Entität, die auf eine andere Entität verweist.</span><span class="sxs-lookup"><span data-stu-id="461f5-144">A property of an entity that references another entity.</span></span> <span data-ttu-id="461f5-145">Z. B. Produkt enthält eine Navigationseigenschaft für die Kategorie und Kategorie enthält eine Navigationseigenschaft für Produkte.</span><span class="sxs-lookup"><span data-stu-id="461f5-145">For example, Product contains a Category navigation property and Category contains a Products navigation property.</span></span>

## <a name="poco"></a><span data-ttu-id="461f5-146">POCO</span><span class="sxs-lookup"><span data-stu-id="461f5-146">POCO</span></span>
<span data-ttu-id="461f5-147">Abkürzung für einfache alte CLR-Objekt.</span><span class="sxs-lookup"><span data-stu-id="461f5-147">Acronym for Plain-Old CLR Object.</span></span> <span data-ttu-id="461f5-148">Eine einfache Klasse, die keine Abhängigkeiten mit jeden Framework enthält.</span><span class="sxs-lookup"><span data-stu-id="461f5-148">A simple user class that has no dependencies with any framework.</span></span> <span data-ttu-id="461f5-149">Im Kontext von Entity Framework eine Entitätsklasse, die nicht von "EntityObject", abgeleitet ist Schnittstellen implementiert oder enthält alle Attribute in EF definiert.</span><span class="sxs-lookup"><span data-stu-id="461f5-149">In the context of EF, a an entity class that does not derive from EntityObject, implements any interfaces or carries any attributes defined in EF.</span></span> <span data-ttu-id="461f5-150">Solche Entitätsklassen, die von der persistenzframework entkoppelt sind werden auch als "Persistenzignoranz".</span><span class="sxs-lookup"><span data-stu-id="461f5-150">Such entity classes that are decoupled from the persistence framework are also said to be "persistence ignorant".</span></span>  

## <a name="relationship-inverse"></a><span data-ttu-id="461f5-151">Beziehung inverse</span><span class="sxs-lookup"><span data-stu-id="461f5-151">Relationship inverse</span></span>
<span data-ttu-id="461f5-152">Die entgegengesetzten Ende einer Beziehung, z. B. Produkt. Kategorie "und" Kategorie ". Das Produkt.</span><span class="sxs-lookup"><span data-stu-id="461f5-152">The opposite end of a relationship, for example, product.Category and category.Product.</span></span>

## <a name="self-tracking-entity"></a><span data-ttu-id="461f5-153">Entität mit selbstnachverfolgung</span><span class="sxs-lookup"><span data-stu-id="461f5-153">Self-tracking entity</span></span>
<span data-ttu-id="461f5-154">Eine Entität aus einer Vorlage für die codegenerierung, die mit N-Tier-Entwicklung unterstützen erstellt.</span><span class="sxs-lookup"><span data-stu-id="461f5-154">An entity built from a code generation template that helps with N-Tier development.</span></span>

## <a name="table-per-concrete-type-tpc"></a><span data-ttu-id="461f5-155">Tabelle pro konkretem Typ (TPC)</span><span class="sxs-lookup"><span data-stu-id="461f5-155">Table-per-concrete type (TPC)</span></span>
<span data-ttu-id="461f5-156">Eine Methode der Zuordnung der Vererbung, wobei jeder nicht abstrakten Typ in der Hierarchie zugeordnet ist, auf die um Tabelle in der Datenbank zu trennen.</span><span class="sxs-lookup"><span data-stu-id="461f5-156">A method of mapping the inheritance where each non-abstract type in the hierarchy is mapped to separate table in the database.</span></span>

## <a name="table-per-hierarchy-tph"></a><span data-ttu-id="461f5-157">Tabelle pro Hierarchie (TPH)</span><span class="sxs-lookup"><span data-stu-id="461f5-157">Table-per-hierarchy (TPH)</span></span>
<span data-ttu-id="461f5-158">Eine Methode der Zuordnung der Vererbung, in dem alle Typen in der Hierarchie auf dieselbe Tabelle in der Datenbank zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="461f5-158">A method of mapping the inheritance where all types in the hierarchy are mapped to the same table in the database.</span></span> <span data-ttu-id="461f5-159">Diskriminator Spalte(n) wird verwendet, um zu identifizieren, welche Art von jeder Zeile zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="461f5-159">A discriminator column(s) is used to identify what type each row is associated with.</span></span>

## <a name="table-per-type-tpt"></a><span data-ttu-id="461f5-160">Tabelle pro Typ (TPT)</span><span class="sxs-lookup"><span data-stu-id="461f5-160">Table-per-type (TPT)</span></span>
<span data-ttu-id="461f5-161">Eine Methode der Zuordnung der Vererbung, in dem die allgemeinen Eigenschaften aller Typen in der Hierarchie auf dieselbe Tabelle in der Datenbank zugeordnet sind, aber die eindeutige Eigenschaften für jeden Typ in eine separate Tabelle zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="461f5-161">A method of mapping the inheritance where the common properties of all types in the hierarchy are mapped to the same table in the database, but properties unique to each type are mapped to a separate table.</span></span>

## <a name="type-discovery"></a><span data-ttu-id="461f5-162">Typermittlung</span><span class="sxs-lookup"><span data-stu-id="461f5-162">Type discovery</span></span>
<span data-ttu-id="461f5-163">Der Prozess zum Identifizieren der Typen, die ein Entity Framework-Modell enthalten sein soll.</span><span class="sxs-lookup"><span data-stu-id="461f5-163">The process of identifying the types that should be part of an Entity Framework model.</span></span>