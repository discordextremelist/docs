[del]: https://discordextremelist.xyz

[allowed_mentions]: https://discord.com/developers/docs/resources/channel#allowed-mentions-object
[allowed_mentions_del]: https://github.com/discordextremelist/help/blob/master/allowed_mentions/en.md

[bot]: https://discordapp.com/developers/docs/resources/user#user-object

[best_practices]: https://github.com/Andre601/discord-bot-best-practices

# Beste Praktiken für Discord Bots
*Diese Richtlinien sind für Bots, welche auf öffentlichen Servern aktiv sind, gedacht. Wenn dein Bot nur auf private Server limitiert ist, wird dieses Dokument sehr wahrscheinlich nicht auf dich zutreffen. Es ist eine **Vorraussetzung**, dass du diese diese Richtlinien befolgst, wenn du deinen Bot auf [Discord Extreme List][del] auflistest.

## Befehlsprefixe
1. **Befehle sollten explizit aufgerufen werden**  
   Bots solten nicht durch normalen Chat aktiviert werden. Verwende stattdessen einen Prefix oder antworte nur, wenn dein Bot direkt `@Erwähnt` wird.
2. **Verwende einzigartige Prefixe**  
   Einzelcharakter Prefixe wie `!`, `$` und `.` sind weit verbreitet um Befehle auszuführen und führen zu überschneidungen mit anderen Bots. Solltest du dich dazu entscheiden, einen Prefix für deinen Bot zu verwenden, solltest du Wörter (`eule`) oder einzigartige Unicode Zeichen (`¨`) verwenden. Du solltest ausserdem das verwenden von `#` oder `@` als Prefixe vermeiden, da diese dazu verwendet werden können, einen Kanal oder Benutzer zu erwähnen. Idealerweise sollte der Prefix deines Bots auf eine Per-Server Ebene änderbar sein, so dass Serverbesitzer sicherstellen können, dass jeder Bot einen eigenen einzigartigen Prefix hat.
3. **Sei nicht gierig**  
   Limitiere dich auf einen kleine anzahl an Prefixen, um eventuelle Konflikte mit anderen Bots zu vermeiden.
4. **Erwähne nicht zu oft**  
   Wenn du direkt auf einen Befehl antwortest, verwende keine Erwähnung, da diese zu endlosen Bot-Antwortschleifen führen kann. Erwähnungen sind in ordnung, wenn ein lange laufender Befehl ausgeführt wird, aber Private Nachrichten sind eine gute alternative.
5. **Verwende keinen `/` Prefix**  
   Wenn dein Bot `/` als Standardprefix hat wird es konflikte mit Discord's aktualisiertem Slash-Befehl UI haben. Dies bedeutet, dass wenn der Server einen Slash-Befehl mit dem selben namen hat, wie z.B. `/ping` wird dieser Befehl für deinen Bot unbrauchbar. Du kannst `/` als ein Backup-Prefix verwenden, aber dies ist nur erlaubt, wenn dein Bot einen Slash-Befehl mit selben namen und selber funktion hat.

## Befehle
1. **Hab einen `hilfe` Befehl**  
   Ein Hilfebefehl, welcher einfach zu verwenden ist, ist notwendig.
2. **Antworte nicht mit "Ungültiger Befehl"**  
   Wenn ein Benutzer einen Befehl verwendet welcher nicht existiert, lass Ihn leise Schiefgehen. Lass deinen Bot nicht darauf antworten mit etwas wie "Ungültiger Befehl". Wenn jedoch der Befehl richtig, die Argumente aber falsch sind, ist es Okay mit "Ungültige Argumente" zu antworten. Wenn es mehr als einen Bot auf dem Server gibt, welche den gleichen Prefix teilen, kann es zu merkwürdigen verwendungen kommen.
3. **Reinige Erwähnungen**  
   Befehle sollten nicht dazu verwendet werden können, um Rollen `@everyone` oder `@here` zu erwähnen. Dies kann man mit `allowed_mentions` (`allowed_mentions` Objekt - [Siehe Referenz][allowed_mentions], [DEL Allowed Mentions Hilfe][allowed_mentions_del]) einstellen.

## API und Verhalten
1. **Sei respektvoll zu Discord's API**  
   Bots welche die Discord API missbrauchen ruinieren dinge für uns alle. Stelle sicher, dass du Frequenzlimits einhälst und verwende die API auf kluge weise. Frage nach wenn du dir unklar über das einfügen von etwas bist.
2. **Ignoriere deine eigenen Nachrichten und die von anderen Bots**  
   Dies hilft endlosschleifen und eventuelle Sicherheitslücken zu vermeiden. Das verwenden eines "Zero width Space" wie `\u200B` oder `\u180E` am Anfang einer Nachricht hilft auch zu verhindern, dass dein Bot Befehle von anderen Bots auslöst. Die Discord API sagt dir, wenn ein Benutzer ein Bot ist (`bot` Eigenschaft vom `User` Object - [Siehe Referenz][bot])
3. **Erlaube NSFA Befehle nur in NSFA-Kanälen**  
   Alle NSFA (Nicht sicher für (die) Arbeit) Befehle/Funktionen sollten nur in (Discord) NSFA-markierten Kanälen funktionieren.
4. **Verwende das Erwähnen des Bots um Benutzern zu helfen**  
   Das Erlauben einer Erwähnung als prefix (`@MeinBot hilfe`) oder herausfinden eines Prefixes durch das erwähnen des Bots (`@MeinBot` oder `@MeinBot Was ist dein Prefix?`) wird Benutzern, welche gerade erst mit deinem Bot starten, loszulegen. (Stelle sicher, dass was auch immer die Nachricht ist, dass sie einfach zu finden ist. Eine gute Art ist es, sie in der Präsenz des Bot anzuzeigen.) Eine Alternative wäre dass "Brute-Forcing" von Punktuations-Charakteren zum finden, welches es jedoch Bots schwer macht, punkt 2 und 3 zu folgen. Ausserdem ist eine Erwähnung der einzigartigste Prefix von allen.

## Über
Wenn du irgendwelche weiteren Ideen oder änderungen für dieses Dokument hast, mache doch bitte einen Pull request.

Geforked von [Andre601/discord-bot-best-practices][best_practices]. Übersetzung: Andre601
