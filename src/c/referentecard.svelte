<script>
    export let referente;
    import moment from "moment/min/moment-with-locales";
    moment.locale("it");
</script>

<div class="card bm--card-equal-height has-background-grey-lighter">
    <header
        class={referente.Stato__c && referente.Stato__c === "Attivo"
            ? "has-background-info"
            : "has-background-danger"}
    >
        <nav class="level">
            <!-- Left side -->
            <div class="level-left">
                <div class="level-item">
                    <p class="card-header-title is-uppercase">
                        {referente.Name} ({referente.Stato__c})
                    </p>
                </div>
            </div>
        </nav>
    </header>
    <div class="card-content">
        <p>
            <span class="has-text-weight-bold mx-2">Ente:</span><span
                >{referente.ente.Name}</span
            >
        </p>
        <p>
            <span class="has-text-weight-bold mx-2">Portafoglio:</span
            >{#if referente.portafoglio === "Asseveratore"}
                <span class="icon is-small is-left">
                    <i class="fas fa-user-shield" />
                </span>
            {:else}
                <span class="icon is-small is-left">
                    <i class="fas fa-user-tie" />
                </span>
            {/if}

            <span class="mx-2">{referente.portafoglio}</span>
        </p>
        <p>
            <span class="has-text-weight-bold mx-2">Nome:</span><span
                >{referente.FirstName}</span
            >
        </p>
        <p>
            <span class="has-text-weight-bold mx-2">Cognome:</span><span
                >{referente.LastName}</span
            >
        </p>

        <p class="my-3">
            <span class="has-text-weight-bold mx-2">Profilo:</span><span
                class={referente.Profilo__c ? "" : ""}
                >{referente.Profilo__c
                    ? referente.Profilo__c
                    : "Responsabile"}</span
            >
        </p>

        <p>
            <span class="has-text-weight-bold mx-2">Telefono:</span><span
                class={referente.MobilePhone ? "" : "has-text-grey"}
                >{referente.MobilePhone
                    ? referente.MobilePhone
                    : "Non disponibile"}</span
            >
        </p>
        <p>
            <span class="has-text-weight-bold mx-2">Email:</span><span
                class={referente.Email ? "" : "has-text-grey"}
                >{referente.Email ? referente.Email : "Non disponibile"}</span
            >
        </p>
        <p>
            <span class="has-text-weight-bold mx-2">Ultima attività:</span><span
                class={referente.LastActivityDate ? "" : "has-text-grey"}
                >{referente.LastActivityDate
                    ? moment(referente.LastActivityDate).format("DD/MM/YYYY")
                    : "Non disponibile"}</span
            >
            <span class="has-text-weight-bold has-text-info"
                >({moment(referente.LastActivityDate)
                    .startOf("day")
                    .fromNow()})</span
            >
        </p>
    </div>
    <!--
                    <footer class="card-footer">
                        <p class="card-footer-item is-size-6">
                            <span>
                                <a href="/plain/avvisi/{misura.Id}"
                                    >Avvisi relativi</a
                                >
                            </span>
                        </p>
                    </footer>
                    -->
</div>

<style>
    .bm--card-equal-height {
        display: flex;
        flex-direction: column;
        height: 100%;
    }
    .bm--card-equal-height .card-footer {
        margin-top: auto;
    }
</style>
