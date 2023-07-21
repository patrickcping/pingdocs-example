# k1vc9enhqp - "Password Recovery Form" - HTTP Connector

**Action** Custom HTML Template

## Configuration

### General Settings

| Setting                | Static Value  | Variable  |  
|------------------------|----------------------------------------|-------------------|
| Select UI Template | *Not configured* | N/a |
| Use Recaptcha Verification | *Not configured* | N/a |
| Challenge | *Not configured* | N/a |

#### Output Fields List

| Property Name  | Preferred Control Type | Preferred Data Type | Value                 | Hashed Visibility | Display Name    |
|----------------|------------------------|---------------------|-----------------------|-------------------|-----------------|
| `recoveryCode` | textField              | string              | *Intentionally Blank* | `false`           | `Recovery Code` |
| `newPassword`  | textField              | string              | *Intentionally Blank* | `true`            | `New Password`  |
| `buttonValue`  | textField              | string              | *No value*            | *No value*        | *No value*      |

#### Form Validation Rules

*None configured*

#### HTML Template

```html
<div class="app-container" style="display: block;">
	<div class="page__content" style="height: 100%;">
		<div class="card card--no-padding">
            <div class="card__content">
                <div class="org-logo">
                    <img class="org-logo__image" src="https://d3uinntk0mqu3p.cloudfront.net/branding/market/a3d073bc-3108-49ad-b96c-404bea59a1d0.png" alt="Company Logo" />
                </div>
                <h1 class="heading" data-id="heading">Enter New Password</h1>
                <h4 class="heading heading--4" data-id="heading" style="text-align: center;">If you have an active account with a valid email address, you will receive an email with a recovery code which you may enter here, along with a new password. If you do not have an account or email, please contact your administrator to recover your password.			</h4>
                <div data-skcomponent="skerror" class="feedback feedback--error sk-alert sk-alert-danger has-text-danger has-background-danger-light" data-skvisibility=""></div>
                <form class="form" id='recoveryCodeForm' data-id="recoveryCodeForm">
                    <div class="field float-label">
                        <input class="text-input float-label__input" data-id="recoveryCode-input" id="recoveryCode" name="recoveryCode" type="text" value="" />
                        <label class="float-label__label" for="recoveryCode">Recovery Code</label>
                    </div>
                    <div class="field float-label">
                        <input class="text-input text-input--pasword float-label__input" data-id="newPassword-input" id="newPassword" name="newPassword" type="password" value="" />
                        <label class="float-label__label" for="newPassword">New Password</label>
                    </div>
                    <div class="control">
                        <button class="field is-primary mt-2 button file-input--button button--primary brand-primary-bg" data-id="button" type="submit" data-skcomponent="skbutton" data-skbuttontype="form-submit" data-skform="recoveryCodeForm" data-skbuttonvalue="submit">
                            Submit
                            <i class="fas fa-forward ml-2"></i>
                        </button>
                    </div>
                </form>
            </div>
		</div>
	</div>
</div>

```

#### CSS

*Not configured*

#### Script

*Not configured*

#### Input Schema

*Not configured*

#### Output Schema

*Not configured*

### Canvas Settings

| Setting                | Static Value  | Variable  |  
|------------------------|----------------------------------------|-------------------|
| Node Title | `Password Recovery Form` | N/a |
| Node Description | *Default* | N/a |
| Node Background Color | *Default* | N/a |
| Expire Authentication Token | *Default* | N/a |
| Expire Flow Instance Cache | *Default* | N/a |
| Expire Node Instance Cache | *Default* | N/a |
| Expire Node Instance Cache List | *Default* | N/a |

## Flow Posture

```mermaid
flowchart TD
    lz4v4r9c4m[Variables] --> A{Action Decision}
    A -->|True| howu8n9hsc[Username/Password Form]
    howu8n9hsc --> B{Action Decision}
    B -->|True| uob50pnvdv[Button Pressed?]
    uob50pnvdv -->|submit| C{Action Decision}
    C -->|True| icv9ot1nro[User Lookup]
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
    subgraph ide1 [Test]
    k1vc9enhqp --> U{Action Decision}
    end
    U -->|True| lo3onszyab[Recover Password]
    lo3onszyab --> V{Action Decision}
    V -->|True| 760w48p7zi
    V -->|False| xe7a3y02pq[Invalid OTP/password]
    

    click lz4v4r9c4m "#lz4v4r9c4m" "Doc"
    click howu8n9hsc "#howu8n9hsc" "Doc"
    click uob50pnvdv "#uob50pnvdv" "Doc"
    click icv9ot1nro "#icv9ot1nro" "Doc"
    click 8m0sspk0ee "#8m0sspk0ee" "Doc"
    click 0mkskx7cez "#0mkskx7cez" "Doc"
    click dnu7jt3sjz "#dnu7jt3sjz" "Doc"
    click 3of58vu7g8 "#3of58vu7g8" "Doc"
    click kkii6sbmvk "#kkii6sbmvk" "Doc"
    click j9ekv98w5p "#j9ekv98w5p" "Doc"
    click 760w48p7zi "#760w48p7zi" "Doc"
    click nf63ecqmal "#nf63ecqmal" "Doc"
    click ldguma4s6x "#ldguma4s6x" "Doc"
    click 7ohg6pe1wu "#7ohg6pe1wu" "Doc"
    click ck1mtmjp5b "#ck1mtmjp5b" "Doc"
    click tqhsdpjiev "#tqhsdpjiev" "Doc"
    click o9qu0nvyje "#o9qu0nvyje" "Doc"
    click qib48jbqzt "#qib48jbqzt" "Doc"
    click fhz3x7ukuh "#fhz3x7ukuh" "Doc"
    click k1vc9enhqp "#k1vc9enhqp" "Doc"
    click lo3onszyab "#lo3onszyab" "Doc"
    click xe7a3y02pq "#xe7a3y02pq" "Doc"
```

### Previous Nodes

* **Node**: "Send Recovery Code" PingOne Connector (ID: [fhz3x7ukuh](./fhz3x7ukuh.md))
  * **Action Decision**: `Any trigger completes`

### Following Nodes

* **Action Decision**: `true`
  * **Node**: "Recover Password" PingOne Connector (ID: [lo3onszyab](./lo3onszyab.md))
