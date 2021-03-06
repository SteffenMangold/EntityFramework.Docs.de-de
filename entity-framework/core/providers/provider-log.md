---
title: Protokoll des Anbieter-Auswirkungen auf die Änderungen – EF Core
author: ajcvickers
ms.author: avickers
ms.date: 08/08/2018
ms.assetid: 7CEF496E-A5B0-4F5F-B68E-529609B23EF9
ms.technology: entity-framework-core
uid: core/providers/provider-log
ms.openlocfilehash: a87eca72aa58487415eea11e4f83de1a19e73506
ms.sourcegitcommit: 5e11125c9b838ce356d673ef5504aec477321724
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50022336"
---
# <a name="provider-impacting-changes"></a>Anbieter-Auswirkungen auf Änderungen

Diese Seite enthält Links zum pull-Anforderungen, die auf das EF Core-Repository, das Autoren von anderen Datenbankanbietern, reagieren möglicherweise erfordern. Die Absicht ist einen Ausgangspunkt für Autoren von vorhandene Drittanbieter-Datenbankanbieter angeben, wenn es sich bei ihren Anbieter zu einer neuen Version zu aktualisieren.

Dieses Protokoll beginnen wir mit Änderungen vom 2.1 und 2.2. Vor dem 2.1 verwendet die [ `providers-beware` ](https://github.com/aspnet/EntityFrameworkCore/labels/providers-beware) und [ `providers-fyi` ](https://github.com/aspnet/EntityFrameworkCore/labels/providers-fyi) Bezeichnungen auf unseren Problemen und Pull-Anforderungen.

## <a name="21-----22"></a>2.1---> 2.2

### <a name="test-only-changes"></a>Änderungen nur im Test

* [https://github.com/aspnet/EntityFrameworkCore/pull/12057](https://github.com/aspnet/EntityFrameworkCore/pull/12057) -Anpassbare SQL Trennzeichen in Tests zulassen
  * Testen von Änderungen, die außerhalb des strict-floating-Point-Vergleiche in BuiltInDataTypesTestBase zu ermöglichen.
  * Test-Änderungen, die Abfragetests erneut mit anderen SQL-Trennzeichen verwendet werden können.
* [https://github.com/aspnet/EntityFrameworkCore/pull/12072](https://github.com/aspnet/EntityFrameworkCore/pull/12072) -DbFunction Tests für die relationale Spezifikation Tests hinzufügen
  * So, dass diese Tests für alle Datenbankanbieter ausgeführt werden können
* [https://github.com/aspnet/EntityFrameworkCore/pull/12362](https://github.com/aspnet/EntityFrameworkCore/pull/12362) -Async testbereinigung
  * Entfernen Sie `Wait` Aufrufe nicht benötigte Async und einige Testmethoden umbenannt
* [https://github.com/aspnet/EntityFrameworkCore/pull/12666](https://github.com/aspnet/EntityFrameworkCore/pull/12666) -Vereinheitlichen der Protokollierung von Test-Infrastruktur
  * Hinzugefügt `CreateListLoggerFactory` und einige vorherige Infrastruktur für die Protokollierung, die Anbieter mit, dass diese Tests reagieren erforderlich ist, wird entfernt
* [https://github.com/aspnet/EntityFrameworkCore/pull/12500](https://github.com/aspnet/EntityFrameworkCore/pull/12500) – Führen Sie weitere Abfragetests, synchrone und asynchrone
  * Testnamen und die faktorisierung geändert hat, müssen die Anbieter mit, dass diese Tests reagieren
* [https://github.com/aspnet/EntityFrameworkCore/pull/12766](https://github.com/aspnet/EntityFrameworkCore/pull/12766) -Umbenennen von Navigationen in das Modell ComplexNavigations
  * Anbieter, die mithilfe dieser Tests möglicherweise reagieren
* [https://github.com/aspnet/EntityFrameworkCore/pull/12141](https://github.com/aspnet/EntityFrameworkCore/pull/12141) -Zurückgeben Sie Kontext an den Pool anstatt in Funktionstests disposing
  * Diese Änderung umfasst einige Tests refactoring Anbieter, zu reagieren ist möglicherweise erforderlich


### <a name="test-and-product-code-changes"></a>Test und Produkt codeänderungen

* [https://github.com/aspnet/EntityFrameworkCore/pull/12109](https://github.com/aspnet/EntityFrameworkCore/pull/12109) -Konsolidieren RelationalTypeMapping.Clone-Methoden
  * Änderungen in 2.1 die RelationalTypeMapping für eine Vereinfachung in abgeleiteten Klassen zulässig. Wir glauben nicht diese für Anbieter wichtige wurde allerdings Anbieter profitieren von dieser Änderung in ihrer abgeleiteten Typ zuordnen von Klassen.
* [https://github.com/aspnet/EntityFrameworkCore/pull/12069](https://github.com/aspnet/EntityFrameworkCore/pull/12069) -Markierten oder benannte Abfragen
  * Fügt die Infrastruktur für die Kennzeichnung von LINQ-Abfragen und having-diese Tags als Kommentare in die SQL-Anweisung angezeigt werden. Dies erfordert möglicherweise die Anbieter, in der SQL-Generierung zu reagieren.
* [https://github.com/aspnet/EntityFrameworkCore/pull/13115](https://github.com/aspnet/EntityFrameworkCore/pull/13115) – Unterstützung von räumlichen Daten über NTS
  * Ermöglicht die Typmappings und Member Übersetzer außerhalb der Anbieter registriert werden
    * Anbieter müssen Basisklasse aufrufen. FindMapping() in ihrer Implementierung ITypeMappingSource, damit es funktioniert
  * Führen Sie dieses Muster zum Hinzufügen von Unterstützung von räumlichen Daten an Ihren Anbieter, die über Anbieter hinweg konsistent ist.
* [https://github.com/aspnet/EntityFrameworkCore/pull/13199](https://github.com/aspnet/EntityFrameworkCore/pull/13199) – Fügen Sie erweiterte Debuggen für die diensterstellung-Anbieter hinzu
  * Ermöglicht das DbContextOptionsExtensions, um eine neue Schnittstelle zu implementieren, mit deren Hilfe können Benutzer zu verstehen, warum der internen Dienstanbieter neu erstellt wird
* [https://github.com/aspnet/EntityFrameworkCore/pull/13289](https://github.com/aspnet/EntityFrameworkCore/pull/13289) -Fügt CanConnect-API für die Verwendung von integritätsprüfungen
  * Dieser Pull Request hinzugefügt, das Konzept der `CanConnect` das von ASP.NET Core-Health verwendet wird überprüft, um festzustellen, ob die Datenbank verfügbar ist. Standardmäßig ruft die relationalen Implementierung nur `Exist`, aber der Anbieter etwas anderes implementieren können, falls erforderlich. Nicht relationale Anbieter müssen zum Implementieren der neuen API in der Reihenfolge für die integritätsprüfung verwendet werden kann.
* [https://github.com/aspnet/EntityFrameworkCore/pull/13306](https://github.com/aspnet/EntityFrameworkCore/pull/13306) -Basis RelationalTypeMapping DbParameter-Größe nicht entsprechend zu aktualisieren
  * Beenden Sie die Größe wird standardmäßig festgelegt, da dies Abschneiden führen kann. Anbieter müssen möglicherweise ihre eigene Logik hinzufügen, wenn die Größe muss festgelegt werden.
* [https://github.com/aspnet/EntityFrameworkCore/pull/13372](https://github.com/aspnet/EntityFrameworkCore/pull/13372) -RevEng: Geben Sie immer Spaltentyp für die decimal-Spalten
  * Konfigurieren Sie immer Spaltentyp für dezimalspalten in eingerüsteten Code und nicht gemäß der Konvention konfigurieren.
  * Anbieter sollten keine Änderungen auf ihrer Seite erforderlich.
* [https://github.com/aspnet/EntityFrameworkCore/pull/13469](https://github.com/aspnet/EntityFrameworkCore/pull/13469) -Fügt CaseExpression zum Generieren von SQL-CASE-Ausdrücke
* [https://github.com/aspnet/EntityFrameworkCore/pull/13648](https://github.com/aspnet/EntityFrameworkCore/pull/13648) -Fügt die Möglichkeit, geben Sie die replikationsdatentyp-Zuordnungen auf SqlFunctionExpression Store Typrückschluss von Argumenten und Ergebnisse zu verbessern.
