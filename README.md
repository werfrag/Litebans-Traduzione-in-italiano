# Litebans-Traduzione-in-italiano
Traduzione in italiano di Litebans

»«
#Iniziare a copiare da qui!
#Traduzione fatta da werfrag.
#
# The following variables can be used in most messages that involve a punishment:
#
# Punishment specific variables
# $id - The ID of the punishment in the database.
# $type - Type of punishment - ban, mute, warn, kick.
# $reason - the reason for the punishment
# $executor - the moderator's name, or their display name (/nick) if this is enabled in the configuration
# $executorUUID - the moderator's UUID
# $permanent - whether this punishment is permanent
# $ipban - whether this is an IP-ban
# $silent - whether this punishment was executed silently (-s)
# $active - whether this punishment is active
#
# Affected player specific variables
# $playerDisplayName - player display name. If display names are not enabled in the configuration or if the player's display name is not available in the message's context, the player's regular name will be used instead.
# $playerName - player name
# $playerUUID - UUID of affected player
# $playerIP - IP of affected player
# $geoip - Country of affected player, requires GeoIP to be enabled in the configuration, won't work with imported bans
#
# Servers
# These variables represent a server.
# If the plugin is installed on Spigot, a server is represented by the "server_name" option in config.yml.
# If the plugin is installed on BungeeCord, a server is represented by their name in the "servers" section in the proxy's config.yml.
# $serverScope - the scope of the punishment (the server(s) it will affect)
# $serverOrigin - the origin of the punishment (the server/subserver it was placed on)
#
# Dates
# Example format: "2017-02-03", depends on time_format
# $dateStart - date the punishment was placed
# $dateEnd - date the punishment will expire, "forever" if permanent
#
# Durations
# Example format: "20 days, 5 hours, 2 minutes". If permanent, "forever", if expired, "expired" (both are configurable).
# $duration - time until expiry
# $originalDuration - the full duration of the punishment.
# $timeSince - time since placement
#
# Configured message variables
# These variables represent messages in this configuration (messages.yml)
# $base - banned_message_base
# $appealMessage - banned_message_appeal_message
#
# Global variables
# $activeBans, $activeMutes, $activeWarnings - total number of global active punishments
# $totalBans, $totalMutes, $totalWarnings, $totalKicks - total number of global punishments (including inactive ones)
#
# Vault-specific variables
# $playerPrefix - Vault chat prefix of affected player
# $playerSuffix - Vault chat suffix of affected player
# $executorPrefix - Vault chat prefix of executor
# $executorSuffix - Vault chat suffix of executor
# Any message can be disabled by setting it to "". Empty messages will not be sent by the plugin.
#
# Hover text requires permission "litebans.json.hover_text" to view, players lacking permission will see messages without hover text.
# JSON examples:
# broadcast_ban: '&e$bannedPlayer &chas been banned. {hoverText: &aHover text here!}'
#
# Hex colors are supported (#000000 - #FFFFFF)
#
# https://docs.oracle.com/javase/tutorial/i18n/format/simpleDateFormat.html
# Example time format with hours + minutes:
# time_format: 'dd/MM/yyyy HH:mm'
time_format: yyyy-MM-dd
history_time_format: yyyy-MM-dd
banned_message_base: |
  &4&lSei stato bannato dal Server!!&f

  &cBannato il: $dateStart
  &cBannato da: $executor
  &cMotivo: $reason&f
banned_message: |-
  $base
  Scade fra: $duration
  $appealMessage
banned_message_permanent: |-
  $base
  Sei bannato permanente!
  $appealMessage
banned_message_appeal_message: ''
banned_message_geoip_blacklist: |-
  &4&lSei bannato dal network!&f

  La tua posizione è blacklistata: $geoip
bungee_switch_banned: |-
  &cSei stato bannato per $serverScope! Motivo:
  $reason
default_ban_reason: Nessun Motivo
default_mute_reason: Nessun Motivo
permission_error: '&cNon hai abbastanza permessi!'
muted: '&cSei stato mutato! ($duration remaining)!'
muted_permanent: '&cSei stato mutato Permanente!'
notify:
  banned_player_join: '&c$player&f sta provando ad entrare nel server, ma è bannato
    per ($duration)!'
  banned_geoip_blacklist: '&c$player&f sta provando ad entrare nel server, ma è blacklistato
    ($geoip)!'
error_no_reason_provided: '&cYou must provide a reason for this punishment!'
error_no_sql_connection: '&cLiteBans non è connesso in un database!!'
error_no_uuid_found: '&cPlayer non trovato.'
error_console_only: '&cQuesto commando può essere utilizato dalla console.'
internal_error: '&cPl Disattivato!.'
duration_limit_error: '&cMassimo tempo: $duration'
warned_join: '&cHai ricevuto un warn'
warned_join_entry: |-
  &4 - Warnato da &c$executor&4: &c$reason
     &4(&c$timeSince ago&4)
command:
  ban:
    usage: '&cUsa: $command [-s] <player> [duration] [motivo]'
    unban_usage: '&cUsa: $command <player>'
    example: ''
    silent_prefix: '&7Silenzioso '
    broadcast_ban: '&c&l[&4&lBan&c&l] &7$executor &fha bannato &7$bannedPlayer &fPer
      ''&7$reason&f'''
    broadcast_tempban: '&c&l[&4&lTempBan&c&l] &7$executor &fha Tempbannato &7$bannedPlayer
      &fper &7$tempDuration per ''&7$reason&f'''
    broadcast_ip_ban: '&c&l[&4&lBan IP&c&l] &7$executor &fHa bannato IP &7$bannedPlayer
      &fPer ''&7$reason&f'''
    broadcast_temp_ip_ban: '&c&l[&4&lTempBan IP&c&l] &7$executor &fHa Tempbannato
      IP &7$bannedIP &7per $tempDuration per ''&7$reason&f'''
    broadcast_unban: '&c&l[&e&lUnban&c&l] &7$executor &fHa unbannato &7$playerName'
    previous_ban_removed: '&aIl precedente ban di $bannedPlayer è stato rimosso.'
    previous_ban_existing: '&c$bannedPlayer è già bannato, e tu non hai abbastanza
      Permessi per rimpiazzare Il ban.'
    unban_queue: '&7Rientra nel network, Sei stato unbannato.'
    error_no_spec: '&cTempo non valido!'
    unban_fail: '&cIl player non risulta bannato!'
    no_override: '&cPlayer è gia bannato!'
    exempt: '&4&lNon puoi bannare $player!'
    cooldown: '&cDevi aspettare $seconds seccondi Per ripetere il Commando.'
    response: ''
  mute:
    usage: '&cUsa: $command [-s] <player> [duration] [reason]'
    unmute_usage: '&cUsa: $command <player>'
    example: ''
    broadcast: '&c&l[&4&lMute&c&l] &7$executor &fha mutato &7$mutedPlayer &fper ''&7$reason&f'''
    broadcast_tempmute: '&c&l[&4&lTempMute&c&l] &7$executor &fha Tempmutato &7$playerName
      &fPer &7$tempDuration &fPer ''&7$reason&f'''
    broadcast_ip_mute: '&c&l[&4&lIpMute&c&l] &7$executor &7Ha Mutato Ip &7$playerName
      &7per ''&7$reason&f'''
    broadcast_temp_ip_mute: '&c&l[&4&lTempIpMute&c&l] &7$executor &fHa TempIpMutato
      &f$mutedIP &fPer &7$tempDuration &fPer ''&7$reason&f'''
    message: |-
      &4Sei stato mutato $executor&4 per &c'&4$reason&c'&4.
      &4Il mute scadrà per $duration.
    message_permanent: |-
      &4Sei stato mutato permanente da $executor&4 per &c'&4$reason&c'&4.
      &4Questo mute non finirà.
    broadcast_unmute: '&c&l[&e&lUnMute&c&l] &7$executor &fha unmutato &7$bannedPlayer'
    unmute_fail: '&cIl player non risulta mutato!'
    no_override: '&cIl player è gia mutato!'
    previous_mute_removed: '&aIl precedente mute di $mutedPlayer è stato rimosso.'
    previous_mute_existing: '&c$mutedPlayer è gia mutato, e tu non hai il permesso
      di rimpiazzare il mute.'
    exempt: '&4&lNon puoi mutare $player!'
    notification: '&c$mutedPlayer sta provando a parlare, ma è mutato.'
    error_not_enabled: '&cMute in config non abbilitato!'
    response: ''
    broadcast_unwarn: '&c&l[&e&lUnWarn&c&l] &7$executor &fHa unwarnato &7$bannedPlayer'
  warn:
    usage: '&cUsa: $command [-s] <player> [reason]'
    unwarn_usage: '&cUsa: $command <player>'
    example: ''
    broadcast: '&c&l[&4&lWarn&c&l] &7$executor &fha wanato &7$warnedPlayer &fper ''&7$reason&f'''
    message: |-
      &cSei stato warnato da $executor&c per &c'$reason&c'.
      &cWarnato per $duration.
    list_entry: '&7 \- Warnato da $executor: ''$reason&f'''
    unwarn_response: '&aL ultimo warn è stato rimosso per $player.'
    unwarn_fail: '&cIl player non ha warn!'
    exempt: '&4&lNon puoi warnare $player!'
    cooldown: '&cDevi aspettare $seconds seccondi before per usare questo commando
      di nuovo.'
    response: ''
  history:
    usage: '&c$command <player> [entries=10]'
    start: '&aHistory di $target (Limite: $limit):'
    ban_entry: |-
      &a -- [&f$timeSince ago&a] --&f
      &f $name è stato &cbannato &fda $executor: '&a$reason&f'
    mute_entry: |-
      &a -- [&f$timeSince ago&a] --&f
      &f $name e' stato &7mutato &fda $executor: '&a$reason&f'
    warn_entry: |-
      &a -- [&f$timeSince ago&a] --&f
      &f $name e' stato &6warnato &fda $executor: '&a$reason&f'
    kick_entry: |-
      &a -- [&f$timeSince ago&a] --&f
      &f $name e'stato &ekickato &fda $executor: '&a$reason&f'
    unban_entry: |2-

       &f$name was &7unbanned &fby $executor.
    unmute_entry: |2-

       &f$name was &7unmuted &fby $executor.
    active_suffix: '&f &a&lAttivo'
    expired_suffix: '&f [&8Finito&f]'
    active_suffix_temp: |-
      &f [&cAttivo&f]
      &fFinisce il $duration.
    error_no_history: '&cNon ho trovato la history.'
    error_no_user: '&cUser not found.'
  warnings:
    usage: '&c$command <player>'
    start: '&eWarn attivi di $target:'
  prunehistory:
    usage: '&c$command <player> [durata]'
    message: '&aHistory pulita!.'
  staffhistory:
    usage: '&c$command <player> [entries=10]'
    start: '&aStaff history di $target (Limite: $limit):'
  staffrollback:
    usage: '&c$command <player> [duration]'
    message: '&aRollback completato, Totale rimosso: $amount'
  banlist:
    start: '&f=== &aPagina &6$page&a di &6$total&f ==='
  iphistory:
    usage: '&c$command <player> [entries=10]'
    start: '&aLogin history for $target (Limit: $limit):'
    entry: '&a - [&f$date&a]&f $name&a:&f $ip'
    error_no_history: '&cNon ho trovato history.'
  dupeip:
    usage: '&c$command <player>'
    start: '&aScannerizzo &a$name&f ip &a$ip&f. &aOnline &7Offline &cBannato'
    start_no_ip: '&fScannerizzo &7$name&f. &aOnline &7Offline &cBannato'
    separator: '&f, '
    online: '&a'
    offline: '&7'
    banned: '&c'
    muted: '&e'
    multiple_addresses: '[$num addresses]'
  ipreport:
    start: '&fScannerizzo &a$num&f online player.. &aOnline &7Offline &cBannato'
    entry: '&f$player&a: $result'
  checkban:
    usage: '&c$command <player>'
    no_ban: '&cPlayer non bananto!'
    banned: |-
      &aPlayer &a$target è bannato:
      &aBannato da: $executor
      &aPer: $reason&a
      &aBanned il: $dateStart
      &aBanned Finisce: $dateEnd ($duration)
      &aBanned sul server &6&a$serverOrigin&a, server scope: &6$serverScope
      &aIP ban: $ipban, silenzioso: $silent, permanente: $permanent
  checkmute:
    usage: '&c$command <player>'
    no_mute: '&cTarget is not muted!'
    muted: |-
      &aTarget &f[&a$target&f]&a is muted:
      &aMuted by: $executor
      &aReason: $reason&r
      &aMuted on: $dateStart
      &aMuted until: $dateEnd ($duration)
      &aMuted on server &6$serverOrigin&a, server scope: &6$serverScope
      &aIP mute: $ipban, silent: $silent, permanent: $permanent
  lastuuid:
    usage: '&c$command <player|IP>'
    message: '&fLast UUID for &a$name&f: &a$uuid'
  geoip:
    usage: '&c$command <player|IP>'
    message: '&a$target&f is from: &a$result'
    error_disabled: '&cGeoIP support is not enabled in the configuration!'
    error_unavailable: '&cGeoIP support is currently unavailable, has it been downloaded
      yet?'
    error_not_found: '&cGeoIP information for $target not found.'
  lockdown:
    usage: '&c$command <reason> | $command end'
    message: '&cServer lockdown activated (reason: "$reason&c")'
    stopped: '&aLockdown has been deactivated.'
    kick_message: |-
      Server lockdown active, try again later.
      Reason: $reason
    kick_message_global: |-
      Network lockdown active, try again later.
      Reason: $reason
    error_not_active: '&cLockdown is not active!'
  kick:
    usage: '&c$command <player> [reason]'
    no_match: '&cErrore: &4Player non trovato.'
    kick_requested: '&6Player $player non è online nel server. kick cross-server
      è stato richiesto.'
    message: 'Kickato da $executor per $reason'
    message_no_reason: Kickato da $executor.
    response: '&6$player è stato kickato .'
    broadcast: '&a$player&f è stato kickato da &a$executor&f per ''&a$reason&f''.'
    broadcast_no_reason: '&a$player&f è stato kickato da &a$executor&f.'
    exempt: '&cNon puoi kickare $player!'
  togglechat:
    toggle_off: '&aLa chat è stata mutata.'
    toggle_on: '&aLa chat è stata unmutata.'
  clearchat:
    broadcast: '&aChat clearata da $executor.'
  mutechat:
    response: '&cServer chat mutata!'
    broadcast_disabled: '&cServer chat mutata da $executor.'
    broadcast_enabled: '&aServer chat unmutata da $executor.'
  litebans:
    reload_success: '&aLiteBans aggiornato correttamente.'
    reload_fail_connect: '&aLitebans reloaded. &cNon ho riuscito a connettermi nel
      database.'
    reload_fail: '&cReload fallito.'
    reload_fail_config: |-
      &c[LiteBans] &4config.yml is not valid and could not be loaded, the default configuration will be used.
      &cPlease check the server console for more information.
    reload_fail_messages: |-
      &c[LiteBans] &4messages.yml is not valid and could not be loaded, default messages will be used.
      &cPlease check the server console for more information.
    add_history_usage: '&c$command addhistory <name> <UUID> <IP>'
    add_history: '&aHistory added.'
    fix_history: '&aFixing history for table $table...'
    fix_history_result: '&aAdded $amount entries.'
    fix_history_offline_uuids: '&c$amount UUIDs were not fetched from Mojang since
      they are offline-mode UUIDs.'
    import_usage: '&c$command import start'
    import_start: '&aImporting from $db, this might take a while...'
    import_finish: '&aImport finished successfully. $bans bans imported, $ipbans IP-bans.'
    import_finish_litebans: '&aImport finished successfully. Added $amount entries
      to the database.'
    import_fail: '&cImport failed. Check console.'
    import_unsupported: '&cImporting from ''$name'' is not supported yet!'
duration:
  expired: Scaduto
  forever: Permanente
  year: anno
  years: anni
  month: mese
  months: mesi
  week: settimana
  weeks: settimana
  day: giorno
  days: giorni
  hour: ora
  hours: ore
  minute: minuto
  minutes: minuti
  second: seccondo
  seconds: seccondi
  format: '%d %s'
  separator: ', '
strings:
  global: global
  'null': undefined
  'true': 'yes'
  'false': 'no'
»«
