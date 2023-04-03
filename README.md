Registering Commands In OnEnabled 
---------------------------------
```
getCommand("fart").setExecutor(new FartCommand());
```


Registering Listner In OnEnabled 
--------------------------------
```
getServer().getPluginManager().registerEvents(new SpawnListner(this), this);
```


Registering Commands in Plugin.yml
----------------------------------
```
commands:
  fart:
    description: Fart bby
    usage: /<command> <player>
```


Register the config.yml In OnEnabled
----------------------------------
```
getConfig().options().copyDefaults();
saveDefaultConfig();
```

Saving Values to Config.yml
----------------------------------
```
plugin.getConfig().set("spawn.x", location.getX());
plugin.saveConfig();
```

Getting Values to Config.yml
----------------------------------
```
plugin.getConfig().get()
```

Set Instant of Plugin Methode
-------------------------------
```
    private final SpawnPlugin plugin;

    public SpawnCommand(SpawnPlugin plugin){
        this.plugin = plugin;  //this is just a constructer
    }
```    

setting the instant of a plugin method is important
 because it determines when the method is executed 
during the plugin lifecycle.you have to put that in
command.java file inside of CommandExecuter Class's 
Code Block Before making plublic boolean on Command

Example Listner
--------------------------------
```
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent e){

    }
```

Example Command
--------------------------------
```
    @Override
    public boolean onCommand(CommandSender sender, Command command, String label, String[] args) {

        if (sender instanceof Player){
            Player player = (Player) sender;

	  } 
    }
```


Example Inventory
--------------------------------
```
Player p = (Player) sender;
Inventory inventory = Bukkit.createInventory(p, 9, ChatColor.RED + "Potato Time");
        ItemStack item = new ItemStack(Material.DIAMOND_HOE, 1);
        ItemMeta itemMeta = item.getItemMeta();
        itemMeta.setDisplayName(ChatColor.GREEN + "click me");
        item.setItemMeta(itemMeta);
        inventory.setItem(0, item);
        p.openInventory(inventory);
```

this thing might be inside of command



Another Inventory Item Example
--------------------------------
```
        ItemStack item2 = new ItemStack(Material.DIAMOND);
        ItemMeta item2meta = item2.getItemMeta();
        item2meta.setDisplayName(ChatColor.AQUA + " " + ChatColor.BOLD + "Shop");
        ArrayList<String> lore = new ArrayList<>();
        lore.add(" ");
        lore.add(ChatColor.WHITE + "buy ranks and");
        lore.add(ChatColor.WHITE + "enhance experience");
        lore.add(" ");
        lore.add(ChatColor.LIGHT_PURPLE + "Click to Visit");
        item2meta.setLore(lore);
        item2meta.addEnchant(Enchantment.DAMAGE_ALL, 10, true);
        item2meta.addItemFlags(ItemFlag.HIDE_ENCHANTS);
        item2meta.addItemFlags(ItemFlag.HIDE_ATTRIBUTES);
        item2.setItemMeta(item2meta);
        inventory.setItem(1, item2);
```



Listner to Inventory Menu
--------------------------------
```
public class MenuLIstner implements Listener {
    @EventHandler
    public void onMenuClick(InventoryClickEvent e){
        if (e.getView().getTitle().equalsIgnoreCase(ChatColor.RED + "Potato Time")){
            if (e.getCurrentItem() == null){
                return;
            }
            if (e.getCurrentItem().getType() == Material.DIAMOND){
                Player p = (Player) e.getView().getPlayer();
                p.sendMessage(ChatColor.AQUA + "" + ChatColor.UNDERLINE + "Visit https://kasun.com");
            }
            e.setCancelled(true);
        }
    }
}
```

