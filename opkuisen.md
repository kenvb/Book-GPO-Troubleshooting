# Opkuisen van GPO's

GPO's schrijven heel veel instellingen weg naar je computer en de registry. Sommige GPO's zoals de _folder redirection_ corrigeren zichzelf als ze gedelete worden of stellen je alleszins de vraag wat ze zouden moeten doen indien ze gedelete worden.

Heel veel GPO's doen dit niet. Zoals je hieronder kan zien, veranderde ik in mijn mapped drive GPO de drive letter. Er werd een 2de mapped drive aangemaakt, maar de oude werd niet verwijderd. 

![](/assets/shares-foutje.PNG)

In geval van mapped drives kun je dit wel bekomen door de juiste opties te kiezen of door de optie op "delete" te zetten in plaats van de group policy zomaar te verwijderen. Alle informatie rond mapped drives vind je [hier ](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770902(v=ws.11))terug. De optie om een mapped drive te verwijderen nadat de GPO is weggehaald, vind je onder de ["common" tab ](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772371%28v%3dws.10%29)terug.