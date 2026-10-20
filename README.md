# Shadowrocket mobile profile

This public repository contains a Shadowrocket-native profile derived from the routing groups and service assignments in the private mihomo-config project. It does not contain proxy nodes, subscription URLs, credentials, or the private project itself.

Region groups use the url-test and policy-regex-filter pattern shown in [lalifeier/Shadowrocket lazy_group.conf](https://github.com/lalifeier/Shadowrocket/blob/main/lazy_group.conf). The group names and routing choices follow this project's policy map.

## Import

1. Add your own proxy subscription or nodes in Shadowrocket. They are separate from this rules profile.
2. In Config, tap + and paste this raw file URL:
   https://raw.githubusercontent.com/sharpBrother/mihomo-config-shadowrocket/main/Shadowrocket.conf
3. Download the profile, select it, and choose Use Config. Set Global Routing to Config.

The region groups scan node names from subscriptions already added to Shadowrocket. Names should include a region label such as US/USA, JP/Japan, HK/Hong Kong, SG/Singapore, or TW/Taiwan. If a subscription uses different labels, adjust the matching policy-regex-filter in Shadowrocket.conf.

## Rule-source mapping

- The profile uses Shadowrocket-format rule lists from blackmatrix7 for service groups and the direct, proxy, LAN, China, China IP, and AdvertisingLite baselines.
- The original Mihomo rule providers use Clash YAML payloads, so their files are not referenced as Shadowrocket RULE-SET files. The native lists retain the same routing categories, but their exact domain coverage can differ from the Mihomo sources.
- OpenAI, Telegram, and Facebook use blackmatrix7's Shadowrocket-format lists in place of the MetaCubeX lists used by Mihomo. The reject baseline maps to AdvertisingLite; private/direct/proxy/IP baselines map to Lan, Direct, Proxy, China, and ChinaIPs lists.
- Bybit, Kraken, Gate.io, and Homebrew are small MetaCubeX sets translated inline because no corresponding Shadowrocket-format lists were found in blackmatrix7. Their source paths are noted in the profile; refresh those lines when updating the profile.
- macOS process-name rules are omitted because this profile targets iOS, where per-app routing is handled through domain, IP, or user-agent rules.

## Scope

The profile preserves the private/Tailscale direct routes and TUN exclusions from the project baseline. Shadowrocket is retained for mobile or non-critical use; concurrent Shadowrocket and Tailscale behavior has not been validated on a device. The project architecture keeps Clash Verge Rev + Mihomo as the primary macOS client.
