<script>
  let todo = [];
  let element;
  let cpt = 0;
</script>

<section class="box">
  <p class="heading">ma TODO liste</p>
  <input
    placeholder="Ajouter un element"
    bind:value={element}
    class="input"
    type="text"
    name=""
    id="add"
  />
  <button
    on:click={() => {
      if (element) {
        let itm = {
          value: element,
          id: "item" + cpt,
        };
        todo.push(itm);
        todo = todo;
        element = "";
        cpt += 1;
      } else {
        alert("Impossible d'ajouter une liste vide");
      }
    }}
    class="add_to_list box button is-white"
  >
    Add to List</button
  >

  <ul class="todo_list">
    {#each todo as item, id}
      <li class="box" id={item.id}>
        {id + 1 + " - " + item.value}
        <span
          on:click={(e) => {
            todo = todo.filter((itm) => {
              // @ts-ignore
              return itm.id != e.target.parentNode.id;
            });
          }}
          class="button is-danger"
          ><svg
            on:click={(e) => {
              todo = todo.filter((itm) => {
                // @ts-ignore
                return itm.id != e.target.parentNode.parentNode.id;
              });
            }}
            style="width:24px;height:24px"
            viewBox="0 0 24 24"
          >
            <path
              fill="currentColor"
              d="M9,3V4H4V6H5V19A2,2 0 0,0 7,21H17A2,2 0 0,0 19,19V6H20V4H15V3H9M7,6H17V19H7V6M9,8V17H11V8H9M13,8V17H15V8H13Z"
            />
          </svg></span
        >
      </li>
    {:else}
      <p style="text-align: center">
        Veuillez ajouter un element<svg
          style="width:24px;height:24px"
          viewBox="0 0 24 24"
        >
          <path
            fill="currentColor"
            d="M3 21V17H10.5C12.43 17 14 15.43 14 13.5V11H10L16 4L22 11H18V13.5C18 17.64 14.64 21 10.5 21H3Z"
          />
        </svg>
      </p>
    {/each}
  </ul>
</section>

<style>
  @import "https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css";

  section {
    min-height: 100vh;
    max-height: 100vh;
    width: 500px;
    display: flex;
    flex-direction: column;
    row-gap: 30px;
    border: 1px solid #aaaa;
    padding: 50px;
    margin: 0 auto;
    background-color: #f5f5f5;
    overflow-y: scroll;
  }

  @media screen and (max-width: 500px) {
    section {
      width: 100%;
    }
  }

  li {
    display: flex;
    align-items: center;
    column-gap: 50px;
    justify-content: space-between;
    cursor: po;
  }
  li:hover {
    background-color: #f5f5f5;
  }

  .todo_list {
    display: flex;
    row-gap: 20px;
    padding: 0;
    flex-direction: column;
  }
  P {
    font-size: 20px;
    font-weight: bold;
  }
  button {
    background-color: #fff;
  }
</style>
