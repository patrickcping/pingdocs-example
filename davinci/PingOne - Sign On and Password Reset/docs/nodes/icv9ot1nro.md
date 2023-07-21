# "User Lookup" - PingOne Connector (ID: icv9ot1nro)

**Action** Find User

## Configuration

### General Settings

| Setting                | Static Value  | Variable  |  
|------------------------|----------------------------------------|-------------------|
| PingOne Attributes | - `username` | N/a |
| Identifier| N/a | `username` from "Username/Password Form" (Node ID: [howu8n9hsc](./howu8n9hsc.md)) |
| Return User Password Status | Disabled | N/a |

### Canvas Settings

| Setting                | Static Value  | Variable  |  
|------------------------|----------------------------------------|-------------------|
| Node Title | `User Lookup` | N/a |
| Node Description | *Not configured* | N/a |
| Node Background Color | *Not configured* | N/a |
| Expire Authentication Token | *Not configured* | N/a |
| Expire Flow Instance Cache | *Not configured* | N/a |
| Expire Node Instance Cache | *Not configured* | N/a |
| Expire Node Instance Cache List | *Not configured* | N/a |

## Flow Posture

```mermaid
flowchart TD
    lz4v4r9c4m[Variables] --> A{Action Decision}
    A -->|True| howu8n9hsc[Username/Password Form]
    howu8n9hsc --> B{Action Decision}
    B -->|True| uob50pnvdv[Button Pressed?]
    uob50pnvdv -->|submit| C{Action Decision}
    subgraph ide1 [Test]
    C -->|True| icv9ot1nro[User Lookup]
    end
    icv9ot1nro --> F{Action Decision}
    F -->|Any Trigger Completes| dnu7jt3sjz[Check Password]
    uob50pnvdv -->|forgotPassword| D{Action Decision}
    D -->|True| 8m0sspk0ee[Username Form]
    uob50pnvdv -->|No Match| E{Action Decision}
    E -->|True| 0mkskx7cez[Unexpected Error]
    dnu7jt3sjz --> G{Action Decision}
    G -->|True| 3of58vu7g8[Functions]
    G -->|False| kkii6sbmvk[Invalid Username/Password]
    3of58vu7g8 -->|MUST_CHANGE_PASSWORD| H{Action Decision}
    3of58vu7g8 -->|PASSWORD_EXPIRED| I{Action Decision} 
    3of58vu7g8 -->|OK| J{Action Decision}
    3of58vu7g8 -->|No Match| K{Action Decision}
    H -->|True| j9ekv98w5p[Reset Password Form]
    I -->|True| j9ekv98w5p
    J -->|True| 760w48p7zi[Create Shadow User]
    K -->|True| nf63ecqmal[Unexpected Password State]
    j9ekv98w5p --> L{Action Decision}
    L -->|True| ldguma4s6x[Reset Password]
    ldguma4s6x --> M{Action Decision}
    M -->|True| 760w48p7zi
    M -->|False| 7ohg6pe1wu[Invalid Password]
    760w48p7zi --> N{Action Decision}
    N -->|True| ck1mtmjp5b[Token Management]
    8m0sspk0ee --> O{Action Decision}
    O -->|True| tqhsdpjiev[Button Pressed?]
    tqhsdpjiev -->|submit| P{Action Decision}
    tqhsdpjiev -->|cancel| Q{Action Decision}
    tqhsdpjiev -->|No Match| R{Action Decision}
    P -->|True| o9qu0nvyje[User Lookup]
    Q -->|True| howu8n9hsc
    R -->|True| qib48jbqzt[Unexpected Error]
    o9qu0nvyje --> S{Action Decision}
    S -->|Any Trigger Completes| fhz3x7ukuh[Send Recovery Code]
    fhz3x7ukuh --> T{Action Decision}
    T -->|Any Trigger Completes| k1vc9enhqp[Password Recovery Form]
    k1vc9enhqp --> U{Action Decision}
    U -->|True| lo3onszyab[Recover Password]
    lo3onszyab --> V{Action Decision}
    V -->|True| 760w48p7zi
    V -->|False| xe7a3y02pq[Invalid OTP/password]
    

    click lz4v4r9c4m "./lz4v4r9c4m.md" "Doc"
    click howu8n9hsc "./howu8n9hsc.md" "Doc"
    click uob50pnvdv "./uob50pnvdv.md" "Doc"
    click icv9ot1nro "./icv9ot1nro.md" "Doc"
    click 8m0sspk0ee "./8m0sspk0ee.md" "Doc"
    click 0mkskx7cez "./0mkskx7cez.md" "Doc"
    click dnu7jt3sjz "./dnu7jt3sjz.md" "Doc"
    click 3of58vu7g8 "./3of58vu7g8.md" "Doc"
    click kkii6sbmvk "./kkii6sbmvk.md" "Doc"
    click j9ekv98w5p "./j9ekv98w5p.md" "Doc"
    click 760w48p7zi "./760w48p7zi.md" "Doc"
    click nf63ecqmal "./nf63ecqmal.md" "Doc"
    click ldguma4s6x "./ldguma4s6x.md" "Doc"
    click 7ohg6pe1wu "./7ohg6pe1wu.md" "Doc"
    click ck1mtmjp5b "./ck1mtmjp5b.md" "Doc"
    click tqhsdpjiev "./tqhsdpjiev.md" "Doc"
    click o9qu0nvyje "./o9qu0nvyje.md" "Doc"
    click qib48jbqzt "./qib48jbqzt.md" "Doc"
    click fhz3x7ukuh "./fhz3x7ukuh.md" "Doc"
    click k1vc9enhqp "./k1vc9enhqp.md" "Doc"
    click lo3onszyab "./lo3onszyab.md" "Doc"
    click xe7a3y02pq "./xe7a3y02pq.md" "Doc"
```

### Previous Nodes

* **Node**: "Button Pressed?" Function Connector (Node ID: [uob50pnvdv](./uob50pnvdv.md))
  * **Condition**: `submit`
    * **Action Decision**: `true`

### Following Nodes

* **Action Decision**: `Any trigger completes`
  * **Node**: "Check Password" PingOne Connector (Node ID: [dnu7jt3sjz](./dnu7jt3sjz.md))

## Data Flow Posture

### Output variables referenced in the flow

The following variables are set as output variables of this node, with any nodes that refer to this variable directly.

* `matchedUser.Id` ([Link](../data/icv9ot1nro_payload_output_matcheduser_id.md))
  * "Check Password" PingOne Connector (Node ID: [dnu7jt3sjz](./dnu7jt3sjz.md))
  * "Reset Password" PingOne Connector (Node ID: [ldguma4s6x](./ldguma4s6x.md))

### Referenced input variables

The following variables are set in nodes earlier in the flow, and are referenced in this node.

* `username` ([Link](../data/howu8n9hsc_payload_output_username.md))
  * "Username/Password Form" HTTP Connector (Node ID: [howu8n9hsc](./howu8n9hsc.md))
