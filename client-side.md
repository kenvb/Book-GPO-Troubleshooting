# Client side
Meestal ga je troubleshooten vanop de client waar het probleem zich voordoet. Hieronder enkele zaken om zeker in het oog te houden

## Gpupdate

Group Policies worden [standaard ](https://technet.microsoft.com/en-us/library/cc975932.aspx "GPO users")tussen de 90 en 120 minuten uitgevoerd. Dus neen, jouw recent aangemaakte GPO is waarschijnlijk nog niet uitgevoerd. Gpupdate versnelt dit proces door group policies meteen binnen te halen.

![](/assets/gpupdate.PNG)

Veel mensen (guilty as charged) voegen meteen de /force parameter toe. Deze haalt alle GPO's opnieuw binnen in plaats van enkel de veranderingen, mogelijk een gevolg van jaren "/force" indoctrinatie.

Bekijk zeker ook de [gpupdate ](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/gpupdate) pagina voor meer info en hoe zaken sneller en automatisch te laten verlopen

## Event viewer

Meestal vind je heel wat nuttige informatie terug in de "Event viewer" van je client. Heel ver moet je zelfs niet zoeken.

![](/assets/GPO.PNG)

De details kunnen ook heel wat verklaren

![](/assets/GPO2.PNG)

In bovenstaand geval had ik mijn path verkeerd geconfigureerd.
Zoals je hier beneden kunt zien: had ik verwezen naar c:\shares. Dit werkt niet voor drive maps, dat moet een UNC-path zijn. Je wil immers dat je client naar je server gaat en niet naar zijn eigen "c:\shares"-folder, die hoogstwaarschijnlijk niet bestaat.

![](/assets/gpo3.PNG)

Zoals hieronder dus

![](/assets/gpo4.PNG)

Je event viewer 100% vertrouwen is ook niet aan te raden, daarom hebben we dus ook nog andere tools ter onze beschikking.

## GPResult

Zoals hierboven gezegd: de event viewer heeft soms ook zo zijn zwakkere momenten. Dit kan gebeuren als je bepaalde GPO's heel vaak editeert (omdat je foute instellingen hebt gebruikt). Hierdoor kan het zijn dat er geen bijkomende foutmeldingen in de event viewer komen.

Een ander probleem dat we kunnen hebben is dat een GPO niet wordt toegepast op onze user of computer en als er iets niet wordt toegepast, kan het ook geen foutmeldingen geven.

[GPResult ](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/gpresult)is een tooltje dat ons toont welke policies er worden toegepast op onze user-, en computeraccount. Meer zelfs, als er fouten zijn, dan kan deze je ook helpen om deze te achterhalen.

Een makkelijk te lezen formaat is een "html rapport"

Deze genereer je door `gpresult /H "documentnaam".htm `uit te voeren op de commandline van je client.

![](/assets/gpresult3.PNG)

Hieronder heb ik alle tabs toegeklapt.

![](/assets/gpresult1.PNG)

Met het openklappen van de instellingen, kunnen we zien welke instellingen de computer verwerkt heeft en eventueel ook of er iets fouts gebeurd is (zoals in onderstaand voorbeeld)

![](/assets/gpresult2.PNG)
