<template>
  <div>
    <img src="img/loader.gif" class="loaded" alt="" v-if="!loaded" />
    <div v-if="loaded">
      <nav
        class="navbar navbar-dark sticky-top bg-dark flex-md-nowrap p-0 shadow"
      >
        <a class="navbar-brand col-md-3 col-lg-2 mr-0 px-3"
          ><img src="img/logo.png" width="100" alt=""
        /></a>
        <button
          class="navbar-toggler position-absolute d-md-none collapsed"
          type="button"
          data-toggle="collapse"
          data-target="#sidebarMenu"
          aria-controls="sidebarMenu"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>

        <ul class="navbar-nav px-3">
          <li class="nav-item text-nowrap">
            <a class="nav-link" style="cursor: pointer">Salir</a>
          </li>
        </ul>
      </nav>

      <div class="container-fluid">
        <div class="row">
          <nav
            id="sidebarMenu"
            class="col-md-3 col-lg-2 d-md-block bg-light sidebar collapse"
          >
            <div class="sidebar-sticky pt-3">
              <ul class="nav flex-column">
                <sequential-entrance>
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer"
                      @click="fnMenuDivisionales()"
                    >
                      <span data-feather="home"></span>
                      <i class="fas fa-caret-square-right"></i>
                      Divisionales <span class="sr-only"></span>
                    </a>
                  </li>
                </sequential-entrance>
                <sequential-entrance v-if="menuDivisionales">
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer; margin-left: 7%"
                      @click="fnmenuCrearDivisional()"
                    >
                      <span data-feather="home"></span>
                      <i class="fas fa-angle-double-right"></i>
                      Crear Divisional <span class="sr-only"></span>
                    </a>
                  </li>
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer; margin-left: 7%"
                      @click="fnmenuVerDivisional()"
                    >
                      <span data-feather="home"></span>
                      <i class="fas fa-angle-double-right"></i>
                      Ver/Editar Divisionales <span class="sr-only"></span>
                    </a>
                  </li>
                </sequential-entrance>
                <sequential-entrance>
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer"
                      @click="fnMenuEquipos()"
                    >
                      <span data-feather="file"></span>
                      <i class="fas fa-caret-square-right"></i>
                      Equipos
                    </a>
                  </li>
                </sequential-entrance>
                <sequential-entrance v-if="menuEquipos">
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer; margin-left: 7%"
                      @click="fnmenuCrearEquipo()"
                    >
                      <span data-feather="home"></span>
                      <i class="fas fa-angle-double-right"></i>
                      Crear Equipo <span class="sr-only"></span>
                    </a>
                  </li>
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer; margin-left: 7%"
                      @click="fnmenuVerEquipos()"
                    >
                      <span data-feather="home"></span>
                      <i class="fas fa-angle-double-right"></i>
                      Ver/Editar Equipos <span class="sr-only"></span>
                    </a>
                  </li>
                </sequential-entrance>
                <sequential-entrance>
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer"
                      @click="fnMenuJugadores()"
                    >
                      <span data-feather="shopping-cart"></span>
                      <i class="fas fa-caret-square-right"></i>
                      Jugadores
                    </a>
                  </li>
                </sequential-entrance>
                <sequential-entrance v-if="menuJugadores">
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer; margin-left: 7%"
                      @click="fnmenuCrearJugador()"
                    >
                      <span data-feather="home"></span>
                      <i class="fas fa-angle-double-right"></i>
                      Crear Jugador <span class="sr-only"></span>
                    </a>
                  </li>
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer; margin-left: 7%"
                      @click="fnmenuEditarJugador()"
                    >
                      <span data-feather="home"></span>
                      <i class="fas fa-angle-double-right"></i>
                      Ver/Editar Jugadores <span class="sr-only"></span>
                    </a>
                  </li>
                </sequential-entrance>
                <sequential-entrance>
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer"
                      @click="fnMenuTorneos()"
                    >
                      <span data-feather="users"></span>
                      <i class="fas fa-caret-square-right"></i>
                      Torneos
                    </a>
                  </li>
                </sequential-entrance>
                <sequential-entrance v-if="menuTorneos">
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer; margin-left: 7%"
                      @click="fnMenuCrearTorneo()"
                    >
                      <span data-feather="home"></span>
                      <i class="fas fa-angle-double-right"></i>
                      Crear Torneo <span class="sr-only"></span>
                    </a>
                  </li>
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      style="cursor: pointer; margin-left: 7%"
                      @click="fnmenuEditarTorneo()"
                    >
                      <span data-feather="home"></span>
                      <i class="fas fa-angle-double-right"></i>
                      Editar/Auditar Torneos <span class="sr-only"></span>
                    </a>
                  </li>
                </sequential-entrance>
              </ul>
            </div>
          </nav>

          <main role="main" v-if="menuCrearJugador">
            <div class="container" style="text-align: center">
              <h1>Crear Jugador</h1>
            </div>

            <div class="row" style="margin-left: 17%">
              <div class="col">
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Nombre"
                    v-model="inpNombreJugador"
                  />
                  <label for="floatingInput">Nombre</label>
                </div>
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Apellido"
                    v-model="inpApellidoJugador"
                  />
                  <label for="floatingInput">Apellido</label>
                </div>
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Cédula de Identidad"
                    v-model="inpCedulaJugador"
                  />
                  <label for="floatingInput">Cédula de Identidad</label>
                </div>
                <div class="alert alert-success" role="alert" v-if="success6">
                  Jugador guardardado con éxito!
                </div>
                <div class="alert alert-danger" role="alert" v-if="wrong2">
                  Error al procesar los datos, por favor asegúrese de completar
                  todos los campos.
                </div>
                <button
                  class="btn btn-success"
                  @click="fnNuevoJugadorGuardar()"
                >
                  Guardar
                  <img src="img/loader.gif" width="30" v-if="loader6" alt="" />
                </button>
              </div>
              <div class="col">
                <div style="margin-bottom: 4%">
                  <select
                    class="form-select"
                    aria-label="Divisional"
                    v-model="select3"
                    @change="fnNuevoJugadorDivisionalSelect()"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstDivisionales"
                      :value="dato.id"
                    >
                      {{ dato.divisional }}
                    </option>
                  </select>
                </div>
                <div>
                  <select
                    class="form-select"
                    aria-label="Default select example"
                    v-model="inpEquipoJugador"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstEquipos"
                      :value="dato.id"
                    >
                      {{ dato.enombre }}
                    </option>
                    <option value="">Jugador Libre</option>
                  </select>
                </div>
              </div>
              <div class="col"></div>
              <div class="col"></div>
            </div>
          </main>

          <main role="main" v-if="menuEditarJugador">
            <div class="container" style="text-align: center">
              <h1>Editar Jugador</h1>
            </div>

            <div class="row" style="margin-left: 17%">
              <div class="col">
                <div style="margin-bottom: 4%">
                  <select
                    class="form-select"
                    aria-label="Divisional"
                    v-model="select3"
                    @change="fnNuevoJugadorDivisionalSelect()"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstDivisionales"
                      :value="dato.id"
                    >
                      {{ dato.divisional }}
                    </option>
                  </select>
                </div>
                <div>
                  <select
                    class="form-select"
                    aria-label="Default select example"
                    v-model="inpEquipoJugador"
                    @change="fnListaJugadores()"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstEquipos"
                      :value="dato.id"
                    >
                      {{ dato.enombre }}
                    </option>
                  </select>
                </div>
                <div class="list-group">
                  <button
                    type="button"
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    :key="dato"
                    v-for="dato in cplstJugadores"
                    @click="fnEditarJugador(dato.id)"
                  >
                    {{ dato.jnombre + " " + dato.japellido }} -
                    <i class="fas fa-edit"></i>
                    <i
                      class="fas fa-trash-alt"
                      style="color: red; margin-left: 20px"
                      @click="eliminar(dato.id)"
                    ></i>
                  </button>
                </div>
              </div>
              <div class="col">
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Nombre"
                    v-model="inpNombreJugador"
                  />
                  <label for="floatingInput">Nombre</label>
                </div>
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Apellido"
                    v-model="inpApellidoJugador"
                  />
                  <label for="floatingInput">Apellido</label>
                </div>
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Cédula de Identidad"
                    v-model="inpCedulaJugador"
                  />
                  <label for="floatingInput">Cédula de Identidad</label>
                </div>
                <div>
                  <div class="alert alert-success" role="alert" v-if="success7">
                    Jugador actualizado con éxito!
                  </div>
                  <div class="alert alert-danger" role="alert" v-if="wrong3">
                    Error al procesar los datos, por favor asegúrese de
                    completar todos los campos.
                  </div>
                  <button
                    class="btn btn-success"
                    @click="fnEditarjugadorGuardar()"
                  >
                    Guardar
                    <img
                      src="img/loader.gif"
                      width="30"
                      v-if="loader7"
                      alt=""
                    />
                  </button>
                </div>
              </div>
              <div class="col"></div>
              <div class="col"></div>
            </div>
          </main>

          <main role="main" v-if="menuCrearDivisional">
            <div class="container" style="text-align: center">
              <h1>Crear Divisional</h1>
            </div>

            <div class="row" style="margin-left: 17%">
              <div class="col">
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="name@example.com"
                    v-model="inpNuevaDivisional"
                  />
                  <label for="floatingInput">Nueva Divisional</label>
                </div>
                <div class="alert alert-success" role="alert" v-if="success1">
                  Divisional creada con éxito!
                </div>
                <div class="alert alert-danger" role="alert" v-if="wrong1">
                  Divisional ya existente, por favor revise los datos
                  ingresados.
                </div>

                <button
                  class="btn btn-success"
                  @click="fnGuardarNuevaDivisional()"
                >
                  Guardar
                </button>
              </div>
              <div class="col"></div>
              <div class="col"></div>
            </div>
          </main>

          <main role="main" v-if="menuVerDivisional">
            <div class="container" style="text-align: center">
              <h1>Ver Divisionales</h1>
            </div>

            <div class="row" style="margin-left: 17%">
              <div class="col">
                <div class="list-group">
                  <button
                    type="button"
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    :key="dato"
                    v-for="dato in cplstDivisionales"
                    @click="fnEditarDivisional(dato.divisional)"
                  >
                    {{ dato.divisional }}
                  </button>
                </div>
              </div>
              <div class="col">
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Divisional a editar"
                    v-model="inpEditDivisional"
                  />
                  <label for="floatingInput"
                    >Seleccione una Divisional a editar</label
                  >
                </div>
                <div class="alert alert-success" role="alert" v-if="success2">
                  Divisional actualizada con éxito!
                </div>
                <div class="alert alert-success" role="alert" v-if="success3">
                  Divisional eliminada con éxito!
                </div>
                <button
                  class="btn btn-primary btn-sm"
                  @click="
                    (inpEditDivisional = ''),
                      (selinpEditDivisional = ''),
                      (success2 = false),
                      (success3 = false)
                  "
                >
                  <i class="fas fa-sync"></i>
                </button>
              </div>
              <div class="col">
                <div style="margin-bottom: 5%">
                  <button
                    class="btn btn-success btn-sm"
                    @click="fnbtnGuardarDivisional()"
                  >
                    Guardar
                    <img
                      src="img/loader.gif"
                      width="30"
                      alt=""
                      v-if="loader2"
                    />
                  </button>
                </div>
                <div>
                  <button
                    class="btn btn-danger btn-sm"
                    @click="fnbtnEliminarDivisional()"
                  >
                    Eliminar
                    <img
                      src="img/loader.gif"
                      width="30"
                      alt=""
                      v-if="loader3"
                    />
                  </button>
                </div>
              </div>
              <div class="col"></div>
            </div>
          </main>

          <main role="main" v-if="menuCrearEquipo">
            <div class="container" style="text-align: center">
              <h1>Crear Equipo</h1>
            </div>
            <div class="row" style="margin-left: 17%">
              <div class="col">
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Nombre del equipo"
                    v-model="inpNombreEquipo"
                  />
                  <label for="floatingInput">Nombre del equipo</label>
                </div>
                <div class="form-floating">
                  <select
                    class="form-select"
                    id="floatingSelect"
                    aria-label="Floating label select example"
                    v-model="selEquipoDivisional"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstDivisionales"
                      :value="dato.id"
                    >
                      {{ dato.divisional }}
                    </option>
                  </select>
                  <label for="floatingSelect">Selecciona una Divisional</label>
                </div>
                <div class="input-group mb-3">
                  <label class="input-group-text" for="inputGroupFile01"
                    >Escudo</label
                  >
                  <input
                    type="file"
                    class="form-control"
                    id="inputGroupFile01"
                    accept=".jpg,.png"
                    ref="inpEscudo"
                    v-on:change="handleFileUpload()"
                  />
                </div>
                <div class="alert alert-success" role="alert" v-if="success4">
                  Equipo guardado con éxito!
                </div>
                <button class="btn btn-success" @click="fnGuardarEquipoNuevo()">
                  Guardar
                  <img src="img/loader.gif" width="30" alt="" v-if="loader4" />
                </button>
              </div>
              <div class="col"></div>
              <div class="col"></div>
              <div class="col"></div>
            </div>
          </main>

          <main role="main" v-if="menuVerEquipos">
            <div class="container" style="text-align: center">
              <h1>Ver / Editar Equipos</h1>
            </div>
            <div class="row" style="margin-left: 17%">
              <div class="col">
                <div class="form-floating">
                  <select
                    class="form-select"
                    id="floatingSelect"
                    aria-label="Floating label select example"
                    v-model="selEquipoDivisional"
                    @change="fnEquipoSelecDivisional()"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstDivisionales"
                      :value="dato.divisional"
                    >
                      {{ dato.divisional }}
                    </option>
                    <option value="">Sin Divisional</option>
                  </select>
                  <label for="floatingSelect">Selecciona una Divisional</label>
                </div>
                <div class="list-group">
                  <button
                    type="button"
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    :key="dato"
                    v-for="dato in cplstEquipos"
                  >
                    {{ dato.enombre }} -
                    <i
                      class="fas fa-edit"
                      style="align: right"
                      @click="fnEditarEquipo(dato.id)"
                    ></i>
                    <i
                      class="fas fa-trash-alt"
                      style="margin-left: 10px; color: red"
                      @click="eliminar(dato.id)"
                    ></i>
                  </button>
                </div>
              </div>
              <div class="col" v-if="!blSelEquipo"></div>
              <div class="col" v-if="blSelEquipo">
                <div v-if="!select1" @click="select1 = true">
                  <h3>{{ opSelEquipo }}</h3>
                </div>
                <div class="form-floating mb-3" v-if="select1">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    :value="opSelEquipo"
                  />
                  <label for="floatingInput">Editar nombre de equipo</label>
                </div>
                <div v-if="!select2">
                  <img :src="imgDefault" width="150" alt="" />
                  <button
                    class="btn btn-danger btn-sm"
                    @click="(select2 = true), fnVerEquiposEliminarImagen()"
                  >
                    <i class="fas fa-window-close"></i>
                  </button>
                </div>

                <div class="mb-3" v-if="select2">
                  <label for="formFileSm" class="form-label"
                    >Seleccionar nueva imágen</label
                  >
                  <input
                    class="form-control form-control-sm"
                    id="formFileSm"
                    accept=".jpg,.png"
                    ref="newEscudo"
                    v-on:change="handleFileUploadNewImage()"
                    type="file"
                  />
                </div>
                <div class="mb-3" v-if="!select2 || select2">
                  <label for="formFileSm" class="form-label"
                    >Cambiar divisional</label
                  >
                  <div class="form-floating">
                    <select
                      class="form-select"
                      id="floatingSelect"
                      aria-label="Floating label select example"
                      v-model="selEquipoDivisional2"
                    >
                      <option
                        :key="dato"
                        v-for="dato in cplstDivisionales"
                        :value="dato.id"
                      >
                        {{ dato.divisional }}
                      </option>
                    </select>
                    <label for="floatingSelect"
                      >Selecciona una Divisional</label
                    >
                  </div>
                </div>
                <div class="mb-3" v-if="!select2 || select2">
                  <label for="formFileSm" class="form-label"
                    >Importar jugadores</label
                  >
                  <select
                    class="form-select"
                    aria-label="Divisional"
                    v-model="select3"
                    @change="fnNuevoJugadorDivisionalSelectImportar()"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstDivisionales"
                      :value="dato.id"
                    >
                      {{ dato.divisional }}
                    </option>
                  </select>

                  <div>
                    <select
                      class="form-select"
                      aria-label="Default select example"
                      v-model="inpEquipoJugador"
                      @change="fnListaJugadoresImportar()"
                    >
                      <option
                        :key="dato"
                        v-for="dato in cplstEquiposImportar"
                        :value="dato.id"
                      >
                        {{ dato.enombre }}
                      </option>
                      <option value="">Jugadores libres</option>
                    </select>
                  </div>

                  <div class="list-group">
                    <button
                      type="button"
                      class="list-group-item list-group-item-action"
                      aria-current="true"
                      :key="dato"
                      v-for="dato in cplstJugadoresImportar"
                    >
                      {{ dato.jnombre + " " + dato.japellido }} -
                      <i
                        class="fas fa-user-plus"
                        style="color: blue"
                        @click="
                          fnImportarJugador(
                            dato.id,
                            dato.jnombre,
                            dato.japellido
                          )
                        "
                      ></i>
                    </button>
                  </div>
                </div>
                <div class="alert alert-success" role="alert" v-if="success5">
                  Datos guardados con éxito!
                </div>
              </div>
              <div class="col" v-if="!blSelEquipo"></div>
              <div class="col" v-if="blSelEquipo">
                <button class="btn btn-success" @click="fnVerEquiposGuardar()">
                  Guardar cambios
                  <img src="img/loader.gif" width="30" alt="" v-if="loader5" />
                </button>
                <div style="margin-top: 300px">
                  <label for="formFileSm" class="form-label">
                    Jugadores a Importar
                    <button
                      class="btn btn-success btn-sm"
                      @click="fnGuardarImportados()"
                    >
                      Importar
                      <img
                        src="img/loader.gif"
                        width="20"
                        alt=""
                        v-if="loader12"
                      />
                    </button>
                  </label>
                </div>
                <div class="list-group">
                  <button
                    type="button"
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    :key="dato"
                    v-for="dato in lstImpJugadores"
                  >
                    {{ dato.nombre + " " + dato.apellido }} -
                    <i
                      class="fas fa-trash-alt"
                      style="color: red; margin-left: 10px"
                      @click="fnEliminarImportado(dato.id)"
                    ></i>
                  </button>
                </div>
              </div>
              <div class="col"></div>
            </div>
          </main>

          <main role="main" v-if="menuCrearTorneo">
            <div class="container" style="text-align: center">
              <h1>Crear Torneo</h1>
            </div>
            <div class="row" style="margin-left: 17%">
              <div class="col">
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Torneo"
                    v-model="inpNombreTorneo"
                  />
                  <label for="floatingInput">Nombre del Torneo</label>
                </div>
                <div class="form-check">
                  <input
                    class="form-check-input"
                    type="radio"
                    name="rdtorneos"
                    id="flexRadioDefault1"
                    @click="inpTorneoExt = false"
                  />
                  <label class="form-check-label" for="flexRadioDefault1">
                    Torneo Corto
                  </label>
                </div>
                <div class="form-check">
                  <input
                    class="form-check-input"
                    type="radio"
                    name="rdtorneos"
                    id="flexRadioDefault2"
                    @click="inpTorneoExt = true"
                    checked
                  />
                  <label class="form-check-label" for="flexRadioDefault2">
                    Torneo Normal
                  </label>
                </div>
                <div style="margin-bottom: 4%" v-if="inpTorneoExt">
                  <select
                    class="form-select"
                    aria-label="Divisional"
                    v-model="select3"
                    @change="inpDivisionalTorneo = select3"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstDivisionales"
                      :value="dato.id"
                    >
                      {{ dato.divisional }}
                    </option>
                  </select>
                </div>
                <div class="alert alert-success" role="alert" v-if="success8">
                  Torneo guardado con éxito!
                </div>
                <div class="alert alert-danger" role="alert" v-if="wrong4">
                  Error al procesar los datos, por favor asegúrese de completar
                  todos los campos.
                </div>
                <div class="alert alert-success" role="alert" v-if="success9">
                  Fecha creada con éxito!
                </div>

                <button
                  class="btn btn-success"
                  style="margin-right: 5px"
                  @click="fnTorneoNuevoGuardar()"
                >
                  Guardar
                  <img src="img/loader.gif" width="30" v-if="loader8" alt="" />
                </button>

                <div style="margin-top: 10px">
                  <button class="btn btn-success" @click="fnMostrarTorneos()">
                    <i class="fas fa-caret-down"></i>
                    Torneos
                  </button>
                </div>
                <div class="list-group">
                  <button
                    type="button"
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    :key="dato"
                    v-for="dato in cplstTorneos"
                    @click="(torneoid = dato.id), (lbltorneo = dato.tnombre)"
                  >
                    {{ dato.tnombre }} -
                    <i class="fas fa-angle-double-right"></i>
                  </button>
                </div>
              </div>
              <div class="col">
                <div v-if="lblfecha != ''">
                  <h5>
                    <button
                      class="btn btn-success btn-sm"
                      @click="fnFechaMenos()"
                    >
                      <i class="fas fa-caret-left"></i></button
                    >{{ lblfecha + " - " + lbltorneo }}
                    <button
                      class="btn btn-success btn-sm"
                      @click="fnFechaMas()"
                    >
                      <i class="fas fa-caret-right"></i>
                    </button>
                  </h5>
                </div>
                <div class="form-floating" v-if="lblfecha != ''">
                  <select
                    class="form-select"
                    id="floatingSelect"
                    aria-label="Floating label select example"
                    v-model="equipoA"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstEquipos"
                      :value="dato.enombre"
                    >
                      {{ dato.enombre }}
                    </option>
                  </select>
                  <label for="floatingSelect">Equipo A</label>
                </div>
                <div class="form-floating" v-if="lblfecha != ''">
                  <select
                    class="form-select"
                    id="floatingSelect"
                    aria-label="Floating label select example"
                    v-model="equipoB"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstEquipos"
                      :value="dato.enombre"
                    >
                      {{ dato.enombre }}
                    </option>
                  </select>
                  <label for="floatingSelect">Equipo B</label>
                </div>
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Torneo hora"
                    v-model="inpTorneoHora"
                  />
                  <label for="floatingInput">Hora</label>
                </div>
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Torneo fecha"
                    v-model="inpTorneoFecha"
                  />
                  <label for="floatingInput">Fecha</label>
                </div>
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Torneo"
                    v-model="inpTorneoChancha"
                  />
                  <label for="floatingInput">Cancha</label>
                </div>
                <div class="alert alert-danger" role="alert" v-if="wrong5">
                  Error al generar fecha, por favor compruebe los campos.
                </div>
                <div class="alert alert-danger" role="alert" v-if="wrong6">
                  Error al generar fecha, por favor elija un torneo.
                </div>
                <button
                  class="btn btn-success"
                  v-if="lblfecha == ''"
                  @click="fnTorneoCrearNuevaFecha()"
                >
                  <i class="far fa-calendar-plus"></i>
                  Agregar Fecha
                </button>
                <button
                  class="btn btn-success"
                  v-if="lblfecha != ''"
                  @click="fnTorneoGuardarPartido()"
                >
                  Guardar Fecha
                  <img src="img/loader.gif" width="30" v-if="loader9" alt="" />
                </button>
                <button
                  class="btn btn-primary"
                  style="margin-left: 5px"
                  @click="fnFechaReset()"
                >
                  <i class="fas fa-undo-alt"></i>
                </button>
                <div class="form-check">
                  <input
                    class="form-check-input"
                    type="radio"
                    name="rdfecha"
                    id="flexRadioDefault1"
                    checked
                    @click="selFechaPartido = true"
                  />
                  <label class="form-check-label" for="flexRadioDefault1">
                    Guardar Nueva Fecha + Partido.
                  </label>
                </div>
                <div class="form-check">
                  <input
                    class="form-check-input"
                    type="radio"
                    name="rdfecha"
                    id="flexRadioDefault2"
                    @click="selFechaPartido = false"
                  />
                  <label class="form-check-label" for="flexRadioDefault2">
                    Guardar Partido en Fecha seleccionada.
                  </label>
                </div>
              </div>
              <div class="col">
                <div v-if="equipoA != ''">
                  <h4>{{ equipoA + " VS " + equipoB }}</h4>
                </div>
                <div style="margin-left: 20%">
                  <h6>{{ "Hora: " + inpTorneoHora }}</h6>
                </div>
                <div style="margin-left: 20%">
                  <h6>{{ "Fecha: " + inpTorneoFecha }}</h6>
                </div>
                <div style="margin-left: 20%">
                  <h6>{{ "Cancha: " + inpTorneoChancha }}</h6>
                </div>
              </div>
              <div class="col"></div>
            </div>
          </main>

          <main role="main" v-if="menuEditarTorneo">
            <div class="container" style="text-align: center">
              <h1>Editar Torneos</h1>
            </div>
            <div class="row" style="margin-left: 17%">
              <div class="col">
                <div style="margin-bottom: 4%" v-if="inpTorneoExt">
                  <select
                    class="form-select"
                    aria-label="Divisional"
                    v-model="select3"
                    @change="fnTorneoSelDivisional(select3)"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstDivisionales"
                      :value="dato.id"
                    >
                      {{ dato.divisional }}
                    </option>
                    <option value="Exclusivo">Torneos Cortos</option>
                  </select>
                </div>
                <div class="list-group">
                  <button
                    type="button"
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    :key="dato"
                    v-for="dato in cplstTorneos"
                    @click="
                      fnTorneoSelFecha(dato.id), (lblSelTorneo = dato.tnombre)
                    "
                  >
                    {{ dato.tnombre }} -
                    <i class="fas fa-angle-double-right"></i>
                  </button>
                </div>
              </div>
              <div class="col">
                <h5>{{ lblSelTorneo }}</h5>
                <div class="list-group">
                  <button
                    type="button"
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    :key="dato"
                    v-for="dato in cplstFechas"
                    @click="
                      fnTorneoSelPartidos(dato.id), (lblSelFecha = dato.fnombre)
                    "
                  >
                    {{ dato.fnombre }} -
                    <i class="fas fa-angle-double-right"></i>
                  </button>
                </div>
              </div>
              <div class="col">
                <h5>{{ lblSelFecha }}</h5>
                <div class="list-group" v-if="lblSelFecha != ''">
                  <button
                    type="button"
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    :key="dato"
                    v-for="dato in lstPartidos"
                    @click="
                      (equipoA = dato.pequipoa),
                        (equipoB = dato.pequipob),
                        (partidoId = dato.id),
                        fnTorneoSelPartidoData(dato.id)
                    "
                  >
                    {{ dato.pequipoa + " - " + dato.pequipob }} -
                    <span
                      class="badge bg-success"
                      v-if="dato.peagoles >= 0 && dato.pebgoles >= 0"
                      >Jugado</span
                    >
                    <i class="fas fa-angle-double-right"></i>
                  </button>
                </div>
              </div>
              <div class="col">
                {{ lblSelPartido }}
                <div class="form-floating mb-3" v-if="lblSelFecha != ''">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    v-model="golesEquipoA"
                  />
                  <label for="floatingInput">{{ "Goles: " + equipoA }}</label>
                </div>
                <div class="form-floating mb-3" v-if="lblSelFecha">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    v-model="golesEquipoB"
                  />
                  <label for="floatingInput">{{ "Goles: " + equipoB }}</label>
                </div>
                <div class="form-floating mb-3" v-if="lblSelFecha != ''">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    v-model="fairPlayEquipoA"
                  />
                  <label for="floatingInput">{{
                    "Fair Play: " + equipoA
                  }}</label>
                </div>
                <div class="form-floating mb-3" v-if="lblSelFecha != ''">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    v-model="fairPlayEquipoB"
                  />
                  <label for="floatingInput">{{
                    "Fair Play: " + equipoB
                  }}</label>
                </div>
                <div class="input-group mb-3" v-if="lblSelFecha != ''">
                  <label class="input-group-text" for="inputGroupFile01"
                    >Fotos:</label
                  >
                  <input
                    type="file"
                    class="form-control"
                    id="inputGroupFile01"
                    ref="fotosPartido"
                    multiple
                  />
                </div>
                <div class="alert alert-success" role="alert" v-if="success10">
                  Datos guardados con exito!
                </div>
                <button
                  class="btn btn-success"
                  @click="fnTorneoGuardarPartidos()"
                >
                  Guardar
                  <img src="img/loader.gif" width="30" v-if="loader10" alt="" />
                </button>

                <button
                  class="btn btn-primary"
                  style="margin-left: 10px"
                  @click="fnPartidoDetalles()"
                >
                  Detalles
                  <i class="fas fa-eye-slash" v-if="!partidoDetalles"></i
                  ><i class="fas fa-eye" v-if="partidoDetalles"></i>
                </button>
                <button
                  type="button"
                  class="btn btn-primary"
                  style="margin-left: 10px"
                  @click="fnEditarPartido()"
                >
                  Editar Partido
                </button>
              </div>
            </div>
            <div class="row" style="margin-left: 17%" v-if="partidoDetalles">
              <div class="col">
                <h6>{{ equipoA }}</h6>
                <div style="margin-bottom: 30px">
                  <select
                    class="form-select"
                    aria-label="Default select example"
                    v-model="jugadorA"
                  >
                    <option selected>Seleccione Jugador</option>
                    <option
                      :key="dato"
                      v-for="dato in cplstJugadoresA"
                      :value="dato.id"
                    >
                      {{ dato.jnombre + " " + dato.japellido }}
                    </option>
                  </select>

                  <select
                    class="form-select"
                    style="width: 25%"
                    aria-label="Default select example"
                    v-model="golesJugadorA"
                  >
                    <option selected>Goles</option>
                    <option value="0">0</option>
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                    <option value="5">5</option>
                    <option value="6">6</option>
                    <option value="7">7</option>
                    <option value="8">8</option>
                    <option value="9">9</option>
                    <option value="10">10</option>
                  </select>
                  <select
                    class="form-select"
                    style="width: 25%"
                    aria-label="Default select example"
                    v-model="sancionesA"
                    :disabled="amonestacionA"
                    @change="fnAmonestacionesA()"
                  >
                    <option selected value="0">Partidos suspendido</option>
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                    <option value="5">5</option>
                    <option value="6">6</option>
                    <option value="7">7</option>
                    <option value="8">8</option>
                    <option value="9">9</option>
                    <option value="10">10</option>
                    <option value="temporada">Temporada</option>
                  </select>
                  <div class="form-check form-switch">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      id="flexSwitchCheckDefault"
                      :checked="chekedA1"
                      @change="
                        (chekedA1 = true),
                          (chekedA2 = false),
                          (chekedA3 = false),
                          (chekedA4 = false)
                      "
                    />
                    <label class="form-check-label" for="flexSwitchCheckDefault"
                      >Amarilla</label
                    >
                  </div>
                  <div class="form-check form-switch">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      id="flexSwitchCheckDefault"
                      :checked="chekedA2"
                      @change="
                        (chekedA1 = false),
                          (chekedA2 = true),
                          (chekedA3 = false),
                          (chekedA4 = false)
                      "
                    />
                    <label class="form-check-label" for="flexSwitchCheckDefault"
                      >Doble Amarilla</label
                    >
                  </div>
                  <div class="form-check form-switch">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      id="flexSwitchCheckDefault"
                      :checked="chekedA3"
                      @change="
                        (chekedA1 = false),
                          (chekedA2 = false),
                          (chekedA3 = true),
                          (chekedA4 = false)
                      "
                    />
                    <label class="form-check-label" for="flexSwitchCheckDefault"
                      >Roja</label
                    >
                  </div>
                  <div class="form-check form-switch">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      id="flexSwitchCheckDefault"
                      :checked="chekedA4"
                      @change="
                        (chekedA1 = false),
                          (chekedA2 = false),
                          (chekedA3 = false),
                          (chekedA4 = true)
                      "
                    />
                    <label class="form-check-label" for="flexSwitchCheckDefault"
                      >Sin Tarjetas</label
                    >
                  </div>
                  <h5>Amonestados</h5>
                  <ul>
                    <li :key="dato" v-for="dato in lstAmonestadosA">
                      {{
                        dato.jnombre +
                        " " +
                        dato.japellido +
                        " - " +
                        dato.amonestaciones +
                        " Partidos restantes"
                      }}
                      <i
                        class="fas fa-check"
                        style="color: green"
                        v-if="descontados"
                      ></i>
                    </li>
                  </ul>
                </div>
                <h6>{{ equipoB }}</h6>
                <div>
                  <select
                    class="form-select"
                    aria-label="Default select example"
                    v-model="jugadorB"
                  >
                    <option selected>Seleccione Jugador</option>
                    <option
                      :key="dato"
                      v-for="dato in cplstJugadoresB"
                      :value="dato.id"
                    >
                      {{ dato.jnombre + " " + dato.japellido }}
                    </option>
                  </select>

                  <select
                    class="form-select"
                    style="width: 25%"
                    aria-label="Default select example"
                    v-model="golesJugadorB"
                  >
                    <option selected>Goles</option>
                    <option value="0">0</option>
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                    <option value="5">5</option>
                    <option value="6">6</option>
                    <option value="7">7</option>
                    <option value="8">8</option>
                    <option value="9">9</option>
                    <option value="10">10</option>
                  </select>
                  <select
                    class="form-select"
                    style="width: 25%"
                    aria-label="Default select example"
                    v-model="sancionesB"
                    :disabled="amonestacionB"
                    @change="fnAmonestacionesB()"
                  >
                    <option selected value="0">Partidos suspendido</option>
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                    <option value="5">5</option>
                    <option value="6">6</option>
                    <option value="7">7</option>
                    <option value="8">8</option>
                    <option value="9">9</option>
                    <option value="10">10</option>
                    <option value="temporada">Temporada</option>
                  </select>
                  <div class="form-check form-switch">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      id="flexSwitchCheckDefault"
                      :checked="chekedB1"
                      @change="
                        (chekedB1 = true),
                          (chekedB2 = false),
                          (chekedB3 = false),
                          (chekedB4 = false)
                      "
                    />
                    <label class="form-check-label" for="flexSwitchCheckDefault"
                      >Amarilla</label
                    >
                  </div>
                  <div class="form-check form-switch">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      id="flexSwitchCheckDefault"
                      :checked="chekedB2"
                      @change="
                        (chekedB1 = false),
                          (chekedB2 = true),
                          (chekedB3 = false),
                          (chekedB4 = false)
                      "
                    />
                    <label class="form-check-label" for="flexSwitchCheckDefault"
                      >Doble Amarilla</label
                    >
                  </div>
                  <div class="form-check form-switch">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      id="flexSwitchCheckDefault"
                      :checked="chekedB3"
                      @change="
                        (chekedB1 = false),
                          (chekedB2 = false),
                          (chekedB3 = true),
                          (chekedB4 = false)
                      "
                    />
                    <label class="form-check-label" for="flexSwitchCheckDefault"
                      >Roja</label
                    >
                  </div>
                  <div class="form-check form-switch">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      id="flexSwitchCheckDefault"
                      :checked="chekedB4"
                      @change="
                        (chekedB1 = false),
                          (chekedB2 = false),
                          (chekedB3 = false),
                          (chekedB4 = true)
                      "
                    />
                    <label class="form-check-label" for="flexSwitchCheckDefault"
                      >Sin Tarjetas</label
                    >
                  </div>
                  <h5>Amonestados</h5>
                  <ul>
                    <li :key="dato" v-for="dato in lstAmonestadosB">
                      {{
                        dato.jnombre +
                        " " +
                        dato.japellido +
                        " - " +
                        dato.amonestaciones +
                        " Partidos restantes"
                      }}
                      <i
                        class="fas fa-check"
                        style="color: green"
                        v-if="descontados"
                      ></i>
                    </li>
                  </ul>
                </div>
                <div class="alert alert-success" role="alert" v-if="success11">
                  Datos guardados con éxito!
                </div>

                <button
                  class="btn btn-success"
                  @click="fnPartidoDetallesGuardar()"
                >
                  Guardar
                  <img src="img/loader.gif" width="30" v-if="loader11" alt="" />
                </button>
                <button
                  class="btn btn-success"
                  @click="fnAplicarSanciones()"
                  :disabled="btnAplicarSanciones"
                >
                  Aplicar Sanciones
                </button>
              </div>
              <div class="col" style="margin-top: 5%">
                <h3>Detalles del partido:</h3>
                <ul>
                  <li
                    :key="dato"
                    v-for="dato in lstDetallesPartido"
                    style="margin-top: 10px"
                  >
                    {{
                      dato.jugador +
                      " - Goles:" +
                      dato.goles +
                      " -Amarillas:" +
                      dato.amarillas
                    }}
                    <button
                      class="btn btn-danger btn-sm"
                      @click="fnEliminar(dato.id)"
                    >
                      Eliminar
                    </button>
                  </li>
                </ul>
              </div>
              <div class="col">
                <h3>Fotos del partido</h3>
                <ul>
                  <li
                    :key="dato"
                    v-for="dato in lstFotosDetalles"
                    style="margin-top: 5px"
                  >
                    <img :src="dato.foto" width="50" alt="" /><button
                      class="btn btn-danger btn-sm"
                      @click="fnEliminar(dato.id)"
                    >
                      Eliminar
                    </button>
                  </li>
                </ul>
                <button
                  class="btn btn-warning btn-sm"
                  @click="fnEliminarTodasFotos()"
                >
                  Eliminar todas las fotos
                </button>
              </div>
              <div class="col" v-if="editarPartido">
                <div class="form-floating">
                  <select
                    class="form-select"
                    id="floatingSelect"
                    aria-label="Floating label select example"
                    v-model="equipoA"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstEquipos"
                      :value="dato.enombre"
                    >
                      {{ dato.enombre }}
                    </option>
                  </select>
                  <label for="floatingSelect">Equipo A</label>
                </div>
                <div class="form-floating">
                  <select
                    class="form-select"
                    id="floatingSelect"
                    aria-label="Floating label select example"
                    v-model="equipoB"
                  >
                    <option
                      :key="dato"
                      v-for="dato in cplstEquipos"
                      :value="dato.enombre"
                    >
                      {{ dato.enombre }}
                    </option>
                  </select>
                  <label for="floatingSelect">Equipo B</label>
                </div>
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Torneo hora"
                    v-model="inpTorneoHora"
                  />
                  <label for="floatingInput">Hora</label>
                </div>
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Torneo fecha"
                    v-model="inpTorneoFecha"
                  />
                  <label for="floatingInput">Fecha</label>
                </div>
                <div class="form-floating mb-3">
                  <input
                    type="text"
                    class="form-control"
                    id="floatingInput"
                    placeholder="Torneo"
                    v-model="inpTorneoChancha"
                  />
                  <label for="floatingInput">Cancha</label>
                </div>
                <button
                  class="btn btn-success"
                  style="margin-right: 5px"
                  @click="fnGuardarCambiosPartido()"
                >
                  Guardar
                </button>
                <button class="btn btn-danger" @click="fnEliminarPartido()">Eliminar Partido</button>
              </div>
            </div>
          </main>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.loaded {
  width: 7%;
  height: auto;
  margin-top: 25%;
  margin-left: 47%;
}

body {
  font-size: 0.875rem;
}

.feather {
  width: 16px;
  height: 16px;
  vertical-align: text-bottom;
}

/*
 * Sidebar
 */
.sidebar {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  z-index: 100; /* Behind the navbar */
  padding: 48px 0 0; /* Height of navbar */
  box-shadow: inset -1px 0 0 rgba(0, 0, 0, 0.1);
}

@media (max-width: 767.98px) {
  .sidebar {
    top: 5rem;
  }
}

.sidebar-sticky {
  position: relative;
  top: 0;
  height: calc(100vh - 48px);
  padding-top: 0.5rem;
  overflow-x: hidden;
  overflow-y: auto; /* Scrollable contents if viewport is shorter than content. */
}

@supports ((position: -webkit-sticky) or (position: sticky)) {
  .sidebar-sticky {
    position: -webkit-sticky;
    position: sticky;
  }
}

.sidebar .nav-link {
  font-weight: 500;
  color: #333;
}

.sidebar .nav-link .feather {
  margin-right: 4px;
  color: #999;
}

.sidebar .nav-link.active {
  color: #007bff;
}

.sidebar .nav-link:hover .feather,
.sidebar .nav-link.active .feather {
  color: inherit;
}

.sidebar-heading {
  font-size: 0.75rem;
  text-transform: uppercase;
}

/*
 * Navbar
 */
.navbar-brand {
  padding-top: 0.75rem;
  padding-bottom: 0.75rem;
  font-size: 1rem;
  background-color: rgba(0, 0, 0, 0.25);
  box-shadow: inset -1px 0 0 rgba(0, 0, 0, 0.25);
}

.navbar .navbar-toggler {
  top: 0.25rem;
  right: 1rem;
}

.navbar .form-control {
  padding: 0.75rem 1rem;
  border-width: 0;
  border-radius: 0;
}

.form-control-dark {
  color: #fff;
  background-color: rgba(255, 255, 255, 0.1);
  border-color: rgba(255, 255, 255, 0.1);
}

.form-control-dark:focus {
  border-color: transparent;
  box-shadow: 0 0 0 3px rgba(255, 255, 255, 0.25);
}
</style>

<script>
import Vue from "vue";
import axios from "axios";
import _ from "lodash";
Object.defineProperty(Vue.prototype, "$_", { value: _ });
import SequentialEntrance from "vue-sequential-entrance";
import "vue-sequential-entrance/vue-sequential-entrance.css";
Vue.use(SequentialEntrance);

class Data {
  constructor(
    /*----- Divisionales-------*/
    divisional,

    /*---- Cuentas de Usuarios ----*/
    user,
    password,
    username,
    userlastname,
    aproved,
    usertype,

    /*---- Jugadores ----- */
    jnombre,
    jimg,
    japellido,
    jcedula,
    jgoles,
    jtarjetasam,
    jtarjetasdam,
    jtarjestasroj,
    jamonestaciones,
    jamonestacionid,
    jfechaamonestacion,
    jfechainicioamonestacion,
    jequipo,

    /*------ Equipos ----- */
    enombre,
    eescudo,
    edivision,

    /*------- Torneos ------*/
    tnombre,
    tdivisional,

    /*------- Fechas -------*/
    fnombre,
    ftorneo,

    /*------- Partidos ------*/
    pfechaid,
    pdate,
    ptime,
    pequipoa,
    pequipob,
    peamarcador,
    pebmarcador,
    peagoles,
    pebgoles,
    pamarillasa,
    pamarillasb,
    projasa,
    projasb,
    pfpa,
    pfpb,
    parbitro,
    pobservaciones,
    pcancha,

    // Estadisticas ///////////////////////////////////////////////////////
    epartidoid,
    eequipo,
    ejugador,
    egoles,
    eamarillas,
    erojas,

    /*------ imagenes ----- */
    imgdiv,
    imgurl
  ) {
    this.divisional = divisional;
    /*---- Cuentas de Usuarios ----*/
    this.user = user;
    this.password = password;
    this.username = username;
    this.userlastname = userlastname;
    this.aproved = aproved;
    this.usertype = usertype;

    /*---- Jugadores ----- */
    this.jnombre = jnombre;
    this.jimg = jimg;
    this.japellido = japellido;
    this.jcedula = jcedula;
    this.jgoles = jgoles;
    this.jtarjetasam = jtarjetasam;
    this.jtarjetasdam = jtarjetasdam;
    this.jtarjestasroj = jtarjestasroj;
    this.jamonestaciones = jamonestaciones;
    this.jamonestacionid = jamonestacionid;
    this.jfechaamonestacion = jfechaamonestacion;
    this.jfechainicioamonestacion = jfechainicioamonestacion;
    this.jequipo = jequipo;

    /*------ Equipos ----- */
    this.enombre = enombre;
    this.eescudo = eescudo;
    this.edivision = edivision;

    /*------- Torneos ------*/
    this.tnombre = tnombre;
    this.tdivisional = tdivisional;

    /*------- Fechas -------*/
    this.fnombre = fnombre;
    this.ftorneo = ftorneo;

    /*------- Partidos ------*/
    this.pfechaid = pfechaid;
    this.pdate = pdate;
    this.ptime = ptime;
    this.pequipoa = pequipoa;
    this.pequipob = pequipob;
    this.peamarcador = peamarcador;
    this.pebmarcador = pebmarcador;
    this.peagoles = peagoles;
    this.pebgoles = pebgoles;
    this.pamarillasa = pamarillasa;
    this.pamarillasb = pamarillasb;
    this.projasa = projasa;
    this.projasb = projasb;
    this.pfpa = pfpa;
    this.pfpb = pfpb;
    this.parbitro = parbitro;
    this.pobservaciones = pobservaciones;
    this.pcancha = pcancha;

    // Estadisticas ///////////////////////////////////////////////////////
    this.epartidoid = epartidoid;
    this.eequipo = eequipo;
    this.ejugador = ejugador;
    this.egoles = egoles;
    this.eamarillas = eamarillas;
    this.erojas = erojas;

    /*------ imagenes ----- */
    this.imgdiv = imgdiv;
    this.imgurl = imgurl;
  }
}

export default {
  data() {
    return {
      data: new Data(),
      datos: [],
      api: "https://meloleague2.herokuapp.com/api",
      apiImg: "https://duraznoleagueimg.herokuapp.com/api/images/add",
      imgDefault: "img/default.png",
      lstDivisionales: [],
      lstEquipos: [],
      lstJugadores: [],
      lstDivisionalesImportar: [],
      lstEquiposImportar: [],
      lstJugadoresImportar: [],
      lstTorneos: [],
      lstFechas: [],
      lstPartidos: [],
      loaded: false,
      imageid: "",
      selecid: "",

      //MENÚ
      menuDivisionales: false,
      menuCrearDivisional: false,
      menuVerDivisional: false,
      menuEquipos: false,
      menuCrearEquipo: false,
      menuVerEquipos: false,
      menuJugadores: false,
      menuCrearJugador: false,
      menuTorneos: false,
      menuEditarJugador: false,
      menuCrearTorneo: false,
      menuEditarTorneo: false,

      //LOADERS
      loader1: false,
      loader2: false,
      loader3: false,
      loader4: false,
      loader5: false,
      loader6: false,
      loader7: false,
      loader8: false,
      loader9: false,
      loader10: false,
      loader11: false,
      loader12: false,

      //ALERTS
      success1: false,
      success2: false,
      success3: false,
      success4: false,
      success5: false,
      success6: false,
      success7: false,
      success8: false,
      success9: false,
      success10: false,
      success11: false,
      wrong1: false,
      wrong2: false,
      wrong3: false,
      wrong4: false,
      wrong5: false,
      wrong6: false,

      //SELECTIONS
      select1: false,
      select2: false,
      select3: "",

      //Divisional Elementos
      inpNuevaDivisional: "",
      inpEditDivisional: "",
      selinpEditDivisional: "",

      //Equipos Elementos
      inpNombreEquipo: "",
      finpEscudo: "",
      lblNombreEquipo: "",
      selEquipoDivisional: "",
      selEquipoDivisional2: "",
      opSelEquipo: "",
      blSelEquipo: false,
      lstImpJugadores: [],

      //Jugador Elementos
      inpNombreJugador: "",
      inpApellidoJugador: "",
      inpCedulaJugador: "",
      inpEquipoJugador: "",
      jugadorId: "",

      //Torneo Elementos
      inpNombreTorneo: "",
      inpDivisionalTorneo: "",
      inpTorneoExt: true,
      continuarFecha: false,
      torneoid: "",
      contFechas: 0,
      txtFecha: "Fecha",
      lblfecha: "",
      lbltorneo: "",
      fechas: [],
      equipoA: "",
      equipoB: "",
      inpTorneoHora: "",
      inpTorneoFecha: "",
      inpTorneoChancha: "",
      selFechaPartido: false,
      fechaId: "",
      partidoId: "",
      lblSelFecha: "",
      lblSelPartido: "",
      lblSelTorneo: "",

      //Partidos Elementos
      golesEquipoA: "",
      golesEquipoB: "",
      amarillasEquipoA: "",
      amarillasEquipoB: "",
      rojasEquipoA: "",
      rojasEquipoB: "",
      fairPlayEquipoA: "",
      fairPlayEquipoB: "",
      partidoDetalles: false,
      lstJugadoresA: [],
      lstJugadoresB: [],
      chekedA1: false,
      chekedA2: false,
      chekedA3: false,
      chekedA4: true,
      chekedB1: false,
      chekedB2: false,
      chekedB3: false,
      chekedB4: true,
      jugadorA: "",
      jugadorB: "",
      golesJugadorA: "",
      golesJugadorB: "",
      sancionesA: "",
      sancionesB: "",
      amonestacionA: true,
      amonestacionB: true,
      idJugadorA: "",
      idJugadorB: "",
      lstAmonestadosA: [],
      lstAmonestadosB: [],
      lstDetallesPartido: [],
      lstFotosDetalles: [],
      descontados: false,
      btnAplicarSanciones: false,
      editarPartido: false,
    };
  },
  created() {
    this.load();
  },

  methods: {
    load() {
      axios.get(this.api).then((res) => {
        this.datos = res.data;
        this.loaded = true;
      });
    },

    fnmenuVerDivisional() {
      if (this.menuVerDivisional) {
        this.menuVerDivisional = false;
      } else {
        this.menuVerDivisional = true;
        this.menuDivisionales = false;
        this.menuCrearDivisional = false;
        this.menuEquipos = false;
        this.menuCrearEquipo = false;
        this.menuVerEquipos = false;
        this.menuJugadores = false;
        this.menuCrearJugador = false;
        this.menuTorneos = false;
        this.menuEditarJugador = false;
        this.menuCrearTorneo = false;
        this.menuEditarTorneo = false;
      }

      this.lstDivisionales = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.divisional || "") {
          this.lstDivisionales.push({ divisional: element.divisional });
          this.lstDivisionales.sort();
        }
      }
    },

    fnbtnGuardarDivisional() {
      this.loader2 = true;
      let id = "";

      if (this.selinpEditDivisional != "Exclusivo") {
        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element.divisional == this.selinpEditDivisional) {
            id = element._id;
            break;
          }
        }

        this.data = new Data();
        this.data.divisional = this.inpEditDivisional;

        axios.put(this.api + "/" + id, this.data).then((res) => {
          console.log(res);
          this.success2 = true;
          axios.get(this.api).then((res) => {
            this.datos = res.data;
            this.loader2 = false;
          });

          this.lstDivisionales = [];

          for (let i = 0; i < this.datos.length; i++) {
            const element = this.datos[i];
            if (element.divisional || "") {
              this.lstDivisionales.push({ divisional: element.divisional });
            }
          }
        });
      } else {
        alert(
          "La divisional 'Exclusivo' es un elemento ineditable, por favor seleccione otra divisional."
        );
        this.loader2 = false;
      }
    },

    fnbtnEliminarDivisional() {
      this.loader3 = true;
      let id = "";

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.divisional == this.selinpEditDivisional) {
          id = element._id;
          break;
        }
      }

      axios.delete(this.api + "/" + id).then((res) => {
        console.log(res);
        this.success3 = true;
        axios.get(this.api).then((res) => {
          this.datos = res.data;
          this.loader3 = false;
        });

        this.lstDivisionales = [];

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element.divisional || "") {
            this.lstDivisionales.push({ divisional: element.divisional });
          }
        }
      });
    },

    fnEditarDivisional(div) {
      for (let i = 0; i < this.lstDivisionales.length; i++) {
        const element = this.lstDivisionales[i];
        if (element.divisional == div) {
          this.inpEditDivisional = element.divisional;
          this.selinpEditDivisional = element.divisional;
          break;
        }
      }
    },

    fnGuardarNuevaDivisional() {
      this.success1 = false;
      this.wrong1 = false;
      this.loader1 = true;
      let validator = true;
      this.data = new Data();
      this.data.divisional = this.inpNuevaDivisional;

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];

        if (element.divisional == this.inpNuevaDivisional) {
          validator = false;
          this.wrong1 = true;
          break;
        }
      }

      if (validator) {
        axios.post(this.api, this.data).then((res) => {
          console.log(res);
          this.loader1 = false;
          this.success1 = true;
          this.load();
        });
      }
    },

    fnMenuDivisionales() {
      if (this.menuDivisionales) {
        this.menuDivisionales = false;
      } else {
        this.menuDivisionales = true;
        this.menuCrearDivisional = false;
        this.menuVerDivisional = false;
        this.menuEquipos = false;
        this.menuCrearEquipo = false;
        this.menuVerEquipos = false;
        this.menuJugadores = false;
        this.menuCrearJugador = false;
        this.menuTorneos = false;
        this.menuEditarJugador = false;
        this.menuCrearTorneo = false;
        this.menuEditarTorneo = false;
      }
    },

    fnMenuEquipos() {
      if (this.menuEquipos) {
        this.menuEquipos = false;
      } else {
        this.menuEquipos = true;
        this.menuDivisionales = false;
        this.menuCrearDivisional = false;
        this.menuVerDivisional = false;
        this.menuCrearEquipo = false;
        this.menuVerEquipos = false;
        this.menuJugadores = false;
        this.menuCrearJugador = false;
        this.menuTorneos = false;
        this.menuEditarJugador = false;
        this.menuCrearTorneo = false;
        this.menuEditarTorneo = false;
      }

      this.lstDivisionales = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.divisional || "") {
          this.lstDivisionales.push({
            divisional: element.divisional,
            id: element._id,
          });
        }
      }
    },

    fnmenuCrearEquipo() {
      if (this.menuCrearEquipo) {
        this.menuCrearEquipo = false;
      } else {
        this.menuCrearEquipo = true;
        this.menuDivisionales = false;
        this.menuCrearDivisional = false;
        this.menuVerDivisional = false;
        this.menuEquipos = false;
        this.menuVerEquipos = false;
        this.menuJugadores = false;
        this.menuCrearJugador = false;
        this.menuTorneos = false;
        this.menuEditarJugador = false;
        this.menuCrearTorneo = false;
        this.menuEditarTorneo = false;
      }
    },

    handleFileUpload() {
      this.finpEscudo = this.$refs.inpEscudo.files[0];
      console.log(this.finpEscudo);
    },

    handleFileUploadNewImage() {
      this.finpEscudo = this.$refs.newEscudo.files[0];
    },

    fnGuardarEquipoNuevo() {
      this.loader4 = true;
      this.success4 = false;
      const equipo = this.inpNombreEquipo;
      let equipoId = "";
      let formData = new FormData();
      let divisionalid;

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.divisional == this.selEquipoDivisional) {
          divisionalid == element._id;
          break;
        }
      }

      this.data = new Data();
      this.data.enombre = equipo;
      this.data.edivision = this.selEquipoDivisional;

      axios.post(this.api, this.data).then((res) => {
        console.log(res);
        axios.get(this.api).then((res) => {
          this.datos = [];
          this.datos = res.data;

          for (let i = 0; i < this.datos.length; i++) {
            const element = this.datos[i];
            if (element.enombre == equipo) {
              equipoId = element._id;
              formData.append("title", equipoId);
              formData.append("image", this.finpEscudo);

              axios.post(this.apiImg, formData).then((res) => {
                console.log(res);
                this.loader4 = false;
                this.success4 = true;
                this.inpNombreEquipo = "";
              });
              break;
            }
          }
        });
      });
    },

    fnmenuVerEquipos() {
      if (this.menuVerEquipos) {
        this.menuVerEquipos = false;
      } else {
        this.menuVerEquipos = true;
        this.menuDivisionales = false;
        this.menuCrearDivisional = false;
        this.menuVerDivisional = false;
        this.menuEquipos = false;
        this.menuCrearEquipo = false;
        this.menuJugadores = false;
        this.menuCrearJugador = false;
        this.menuTorneos = false;
        this.menuEditarJugador = false;
        this.menuCrearTorneo = false;
        this.menuEditarTorneo = false;
      }
    },

    fnEditarEquipo(id) {
      this.select1 = false;
      this.select2 = false;
      this.selecid = id;

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element._id == id) {
          this.opSelEquipo = element.enombre;
          this.blSelEquipo = true;
          break;
        }
      }

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.title == id) {
          this.imgDefault = element.imageURL;
          break;
        }
      }
    },

    fnVerEquiposGuardar() {
      this.loader5 = true;
      this.success5 = false;
      let nuevaDivision = "";

      if (this.selEquipoDivisional2 == "") {
        nuevaDivision = this.selEquipoDivisional;
      } else {
        nuevaDivision = this.selEquipoDivisional2;
      }

      if (this.select1 && this.select2) {
        this.data = new Data();
        this.data.enombre = this.opSelEquipo;
        this.data.edivision = nuevaDivision;

        axios.put(this.api + "/" + this.selecid, this.data).then((res) => {
          console.log(res);
        });

        let formdata = new FormData();

        formdata.append("title", this.selecid);
        formdata.append("image", this.finpEscudo);

        axios.post(this.apiImg, formdata).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = res.data;
            this.loader5 = false;
          });
        });
      }

      if (!this.select1 && this.select2) {
        console.log("Actualizando imagen...");
        let formdata = new FormData();

        formdata.append("title", this.selecid);
        formdata.append("image", this.finpEscudo);

        axios.post(this.apiImg, formdata).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = res.data;
            this.loader5 = false;
          });
        });
      }

      if (this.select1 && !this.select2) {
        this.data = new Data();
        this.data.enombre = this.opSelEquipo;
        this.data.edivision = nuevaDivision;

        axios.put(this.api + "/" + this.selecid, this.data).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = res.data;
            this.loader5 = false;
            this.success5 = true;
          });
        });
      }

      if (!this.select1 && !this.select2) {
        this.data = new Data();
        this.data.edivision = nuevaDivision;

        axios.put(this.api + "/" + this.selecid, this.data).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = res.data;
            this.loader5 = false;
            this.success5 = true;
          });
        });
      }
    },

    fnVerEquiposEliminarImagen() {
      let id = "";

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.title == this.selecid) {
          id = element._id;
          axios.delete(this.api + "/" + id).then((res) => {
            console.log(res);
          });
          break;
        }
      }
    },

    fnEquipoSelecDivisional() {
      const seleccion = this.selEquipoDivisional;
      let id = "";
      this.lstEquipos = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.divisional == seleccion) {
          id = element._id;
          break;
        }
      }

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.edivision == id) {
          this.lstEquipos.push({ enombre: element.enombre, id: element._id });
        }
      }
    },

    fnMenuJugadores() {
      if (this.menuJugadores) {
        this.menuJugadores = false;
      } else {
        this.menuJugadores = true;
        this.menuDivisionales = false;
        this.menuCrearDivisional = false;
        this.menuVerDivisional = false;
        this.menuEquipos = false;
        this.menuCrearEquipo = false;
        this.menuVerEquipos = false;
        this.menuCrearJugador = false;
        this.menuTorneos = false;
        this.menuEditarJugador = false;
        this.menuCrearTorneo = false;
        this.menuEditarTorneo = false;
      }

      this.lstDivisionales = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.divisional || "") {
          this.lstDivisionales.push({
            divisional: element.divisional,
            id: element._id,
          });
          this.lstDivisionales.sort();
        }
      }
    },

    fnmenuCrearJugador() {
      if (this.menuCrearJugador) {
        this.menuCrearJugador = false;
      } else {
        this.menuCrearJugador = true;
        this.menuDivisionales = false;
        this.menuCrearDivisional = false;
        this.menuVerDivisional = false;
        this.menuEquipos = false;
        this.menuCrearEquipo = false;
        this.menuVerEquipos = false;
        this.menuJugadores = false;
        this.menuTorneos = false;
        this.menuEditarJugador = false;
        this.menuCrearTorneo = false;
        this.menuEditarTorneo = false;
      }
    },

    fnNuevoJugadorDivisionalSelect() {
      this.lstEquipos = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.edivision == this.select3) {
          this.lstEquipos.push({ enombre: element.enombre, id: element._id });
        }
      }
    },

    fnNuevoJugadorDivisionalSelectImportar() {
      this.lstEquiposImportar = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.edivision == this.select3) {
          this.lstEquiposImportar.push({
            enombre: element.enombre,
            id: element._id,
          });
        }
      }
    },

    fnNuevoJugadorGuardar() {
      this.loader6 = true;
      this.success6 = false;
      this.wrong2 = false;

      if (
        this.inpNombreJugador != "" &&
        this.inpApeliidoJugador != "" &&
        this.inpCedulaJugador != "" &&
        this.inpEquipoJugador != ""
      ) {
        this.data = new Data();
        this.data.jnombre = this.inpNombreJugador;
        this.data.japellido = this.inpApellidoJugador;
        this.data.jcedula = this.inpCedulaJugador;
        this.data.jequipo = this.inpEquipoJugador;

        axios.post(this.api, this.data).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = res.data;
            this.loader6 = false;
            this.success6 = true;
            this.inpNombreJugador = "";
            this.inpApellidoJugador = "";
            this.inpCedulaJugador = "";
          });
        });
      } else {
        this.loader6 = false;
        this.wrong2 = true;
      }
    },

    fnEditarJugador(id) {
      this.jugadorId = id;

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element._id == id) {
          this.inpNombreJugador = element.jnombre;
          this.inpApellidoJugador = element.japellido;
          this.inpCedulaJugador = element.jcedula;
        }
      }
    },

    fnEditarjugadorGuardar() {
      this.loader7 = true;
      this.success7 = false;
      this.wrong3 = false;

      if (
        this.inpNombreJugador != "" &&
        this.inpApellidoJugador != "" &&
        this.inpCedulaJugador != ""
      ) {
        this.data = new Data();
        this.data.jnombre = this.inpNombreJugador;
        this.data.japellido = this.inpApellidoJugador;
        this.data.jcedula = this.inpCedulaJugador;

        axios.put(this.api + "/" + this.jugadorId, this.data).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = res.data;
            this.loader7 = false;
            this.success7 = true;
            this.inpNombreEquipo = "";
            this.inpApellidoJugador = "";
            this.inpCedulaJugador = "";
          });
        });
      } else {
        this.loader7 = false;
        this.wrong3 = true;
      }
    },

    fnListaJugadores() {
      this.lstJugadores = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.jequipo == this.inpEquipoJugador) {
          this.lstJugadores.push({
            jnombre: element.jnombre,
            japellido: element.japellido,
            jcedula: element.jcedula,
            jequipo: element.jequipo,
            id: element._id,
          });
        }
      }
    },

    fnListaJugadoresImportar() {
      this.lstJugadoresImportar = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.jequipo == this.inpEquipoJugador) {
          this.lstJugadoresImportar.push({
            jnombre: element.jnombre,
            japellido: element.japellido,
            jcedula: element.jcedula,
            jequipo: element.jequipo,
            id: element._id,
          });
        }
      }
    },

    fnmenuEditarJugador() {
      if (this.menuEditarJugador) {
        this.menuEditarJugador = false;
      } else {
        this.menuEditarJugador = true;
        this.menuDivisionales = false;
        this.menuCrearDivisional = false;
        this.menuVerDivisional = false;
        this.menuEquipos = false;
        this.menuCrearEquipo = false;
        this.menuVerEquipos = false;
        this.menuJugadores = false;
        this.menuCrearJugador = false;
        this.menuTorneos = false;
        this.menuCrearTorneo = false;
        this.menuEditarTorneo = false;
      }
    },

    fnmenuCrearDivisional() {
      if (this.menuCrearDivisional) {
        this.menuCrearDivisional = false;
      } else {
        this.menuCrearDivisional = true;
        this.menuDivisionales = false;
        this.menuVerDivisional = false;
        this.menuEquipos = false;
        this.menuCrearEquipo = false;
        this.menuVerEquipos = false;
        this.menuJugadores = false;
        this.menuCrearJugador = false;
        this.menuTorneos = false;
        this.menuEditarJugador = false;
        this.menuCrearTorneo = false;
        this.menuEditarTorneo = false;
      }
    },

    fnMenuTorneos() {
      if (this.menuTorneos) {
        this.menuTorneos = false;
      } else {
        this.menuTorneos = true;
        this.menuDivisionales = false;
        this.menuCrearDivisional = false;
        this.menuVerDivisional = false;
        this.menuEquipos = false;
        this.menuCrearEquipo = false;
        this.menuVerEquipos = false;
        this.menuJugadores = false;
        this.menuCrearJugador = false;
        this.menuEditarJugador = false;
        this.menuCrearTorneo = false;
        this.menuEditarTorneo = false;
      }

      this.lstDivisionales = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.divisional || "") {
          this.lstDivisionales.push({
            divisional: element.divisional,
            id: element._id,
          });
        }
      }
    },

    fnMenuCrearTorneo() {
      if (this.menuCrearTorneo) {
        this.menuCrearTorneo = false;
      } else {
        this.menuCrearTorneo = true;
        this.menuDivisionales = false;
        this.menuCrearDivisional = false;
        this.menuVerDivisional = false;
        this.menuEquipos = false;
        this.menuCrearEquipo = false;
        this.menuVerEquipos = false;
        this.menuJugadores = false;
        this.menuCrearJugador = false;
        this.menuTorneos = false;
        this.menuEditarJugador = false;
        this.menuEditarTorneo = false;
      }
    },

    fnTorneoNuevoGuardar() {
      this.loader8 = true;
      this.success8 = false;
      this.wrong4 = false;

      if (this.inpTorneoExt && this.inpNombreTorneo != "") {
        this.data = new Data();
        this.data.tnombre = this.inpNombreTorneo;
        this.data.tdivisional = this.inpDivisionalTorneo;

        axios.post(this.api, this.data).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = res.data;
            this.loader8 = false;
            this.success8 = true;

            this.lstEquipos = [];

            for (let i = 0; i < this.datos.length; i++) {
              const element = this.datos[i];
              if (element.edivision == this.inpDivisionalTorneo) {
                this.lstEquipos.push({
                  enombre: element.enombre,
                  id: element._id,
                });
              }
            }

            for (let i = 0; i < this.datos.length; i++) {
              const element = this.datos[i];
              if (element.tnombre == this.inpDivisionalTorneo) {
                this.torneoid = element._id;
              }
            }
          });
        });
      }

      if (!this.inpTorneoExt && this.inpNombreTorneo != "") {
        this.data = new Data();
        this.data.tnombre = this.inpNombreTorneo;
        this.data.tdivisional = "Exclusivo";

        axios.post(this.api, this.data).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            (this.datos = res.data), (this.loader8 = false);
            this.success8 = true;

            this.lstEquipos = [];

            for (let i = 0; i < this.datos.length; i++) {
              const element = this.datos[i];
              if (element.edivision || "") {
                this.lstEquipos.push({
                  enombre: element.enombre,
                  id: element._id,
                });
              }
            }
          });
        });
      }

      if (this.inpNombreTorneo == "") {
        this.loader8 = false;
        this.wrong4 = true;
      }
    },

    fnTorneoCrearNuevaFecha() {
      this.contFechas++;
      this.lblfecha = this.txtFecha + " " + this.contFechas;
      let divisional = "";

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element._id == this.torneoid) {
          divisional = element.tdivisional;
          break;
        }
      }

      if (divisional == "Exclusivo") {
        this.lstEquipos = [];

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element.enombre || "") {
            this.lstEquipos.push({
              enombre: element.enombre,
              id: element._id,
            });
          }
        }
      } else {
        this.lstEquipos = [];

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element.edivision == divisional) {
            this.lstEquipos.push({
              enombre: element.enombre,
              id: element._id,
            });
          }
        }
      }
    },

    fnMostrarTorneos() {
      if (this.inpTorneoExt) {
        this.lstTorneos = [];

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element.tdivisional == this.inpDivisionalTorneo) {
            this.lstTorneos.push({
              tnombre: element.tnombre,
              id: element._id,
            });
          }
        }
      }

      if (!this.inpTorneoExt) {
        this.lstTorneos = [];

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element.tdivisional == "Exclusivo") {
            this.lstTorneos.push({
              tnombre: element.tnombre,
              id: element._id,
            });
          }
        }
      }
    },

    fnFechaMas() {
      this.contFechas++;

      this.lblfecha = this.txtFecha + " " + this.contFechas;
    },

    fnFechaMenos() {
      this.contFechas--;

      if (this.contFechas < 0) {
        this.contFechas = 0;
      }

      this.lblfecha = this.txtFecha + " " + this.contFechas;
    },

    fnFechaReset() {
      this.contFechas = 0;
      this.lblfecha = "";
      this.equipoA = "";
      this.equipoB = "";
    },

    fnTorneoGuardarPartido() {
      this.loader9 = true;
      this.wrong6 = false;
      this.wrong5 = false;
      let verificado = false;
      let completado = false;
      let equipoAchek = true;
      let equipoBchek = true;
      let fechaChek = true;
      let torneoFechas = [];
      let partidos = [];

      if (
        this.equipoA != "" &&
        this.equipoB != "" &&
        this.inpTorneoHora != "" &&
        this.inpTorneoFecha != "" &&
        this.inpTorneoChancha != ""
      ) {
        completado = true;
      }

      if (this.torneoid != "") {
        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element.ftorneo == this.torneoid) {
            torneoFechas.push({
              fnombre: element.fnombre,
              id: element._id,
            });
          }
        }
        console.log(torneoFechas);
      } else {
        this.wrong6 = true;
      }

      if (torneoFechas.length > 0) {
        let z = 0;
        do {
          for (let i = 0; i < this.datos.length; i++) {
            const element = this.datos[i];
            if (element.pfechaid == torneoFechas[z].id) {
              partidos.push({
                pequipoa: element.pequipoa,
                pequipob: element.pequipob,
              });
            }
          }
          z++;
        } while (z < torneoFechas.length);
      }

      if (partidos.length > 0) {
        for (let i = 0; i < torneoFechas.length; i++) {
          const element = torneoFechas[i];
          if (element.fnombre == this.lblfecha) {
            this.fechaId = element.id;
            fechaChek = false;
            break;
          }
        }
      }

      if (equipoAchek && equipoBchek && completado) {
        verificado = true;
      }

      if (this.equipoA == this.equipoB) {
        verificado = false;
      }

      if (verificado && this.selFechaPartido && fechaChek) {
        this.data = new Data();
        this.data.fnombre = this.lblfecha;
        this.data.ftorneo = this.torneoid;

        axios.post(this.api, this.data).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = res.data;
            for (let i = 0; i < this.datos.length; i++) {
              const element = this.datos[i];
              if (element.ftorneo == this.torneoid) {
                torneoFechas.push({
                  fnombre: element.fnombre,
                  id: element._id,
                });
              }
            }

            for (let i = 0; i < torneoFechas.length; i++) {
              const element = torneoFechas[i];
              if (element.fnombre == this.lblfecha) {
                this.fechaId = element.id;
                fechaChek = false;
                break;
              }
            }

            this.data = new Data();
            this.data.pfechaid = this.fechaId;
            this.data.pdate = this.inpTorneoFecha;
            this.data.ptime = this.inpTorneoHora;
            this.data.pcancha = this.inpTorneoChancha;
            this.data.pequipoa = this.equipoA;
            this.data.pequipob = this.equipoB;

            axios.post(this.api, this.data).then((res) => {
              console.log(res);
              axios.get(this.api).then((res) => {
                this.datos = res.data;
                this.loader9 = false;
                this.success9 = true;
                this.inpTorneoHora = "";
                this.inpTorneoFecha = "";
                this.inpTorneoChancha = "";
              });
            });
          });
        });
      }

      if (verificado && !this.selFechaPartido && !fechaChek) {
        this.data = new Data();
        this.data.pfechaid = this.fechaId;
        this.data.pdate = this.inpTorneoFecha;
        this.data.ptime = this.inpTorneoHora;
        this.data.pcancha = this.inpTorneoChancha;
        this.data.pequipoa = this.equipoA;
        this.data.pequipob = this.equipoB;

        axios.post(this.api, this.data).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = res.data;
            this.loader9 = false;
            this.success9 = true;
            this.inpTorneoHora = "";
            this.inpTorneoFecha = "";
            this.inpTorneoChancha = "";
          });
        });
      }

      console.log(fechaChek + " - " + equipoAchek + " - " + equipoBchek);

      if (!verificado) {
        this.wrong5 = true;
        this.loader9 = false;
      }
    },
    fnmenuEditarTorneo() {
      if (this.menuEditarTorneo) {
        this.menuEditarTorneo = false;
      } else {
        this.menuEditarTorneo = true;
        this.menuDivisionales = false;
        this.menuCrearDivisional = false;
        this.menuVerDivisional = false;
        this.menuEquipos = false;
        this.menuCrearEquipo = false;
        this.menuVerEquipos = false;
        this.menuJugadores = false;
        this.menuCrearJugador = false;
        this.menuTorneos = false;
        this.menuEditarJugador = false;
        this.menuCrearTorneo = false;
      }
    },
    fnTorneoSelDivisional(id) {
      this.lstTorneos = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.tdivisional == id) {
          this.lstTorneos.push({
            tnombre: element.tnombre,
            id: element._id,
          });
        }
      }
    },

    fnTorneoSelFecha(id) {
      this.lstFechas = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.ftorneo == id) {
          this.lstFechas.push({
            fnombre: element.fnombre,
            id: element._id,
          });
        }
      }
    },

    fnTorneoSelPartidos(id) {
      this.fechaId = id;
      this.lstPartidos = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.pfechaid == id) {
          this.lstPartidos.push({
            pequipoa: element.pequipoa,
            pequipob: element.pequipob,
            peagoles: element.peagoles,
            pebgoles: element.pebgoles,
            pamarillasa: element.pamarillasa,
            pamarillasb: element.pamarillasb,
            projasa: element.projasa,
            projasb: element.projasb,
            id: element._id,
          });
        }
      }
    },

    fnTorneoSelPartidoData(id) {
      this.lstDetallesPartido = [];
      this.lstFotosDetalles = [];
      this.lstJugadoresA = [];
      this.lstJugadoresB = [];
      let equipoA = "";
      let equipoB = "";
      let idA = "";
      let idB = "";
      let jugadorid = "";
      let jugador = "";

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.epartidoid == this.partidoId) {
          jugadorid = element.ejugador;
          for (let i = 0; i < this.datos.length; i++) {
            const element = this.datos[i];
            if (element._id == jugadorid) {
              jugador = element.jnombre + " " + element.japellido;
            }
          }
          this.lstDetallesPartido.push({
            id: element._id,
            jugador: jugador,
            goles: element.egoles,
            amarillas: element.eamarillas,
          });
        }
      }

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.title == this.partidoId) {
          this.lstFotosDetalles.push({
            id: element._id,
            foto: element.imageURL,
          });
        }
      }

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element._id == id) {
          this.lblSelPartido = element.pequipoa + " - " + element.pequipob;
          this.golesEquipoA = element.peagoles;
          this.golesEquipoB = element.pebgoles;
          this.fairPlayEquipoA = element.pfpa;
          this.fairPlayEquipoB = element.pfpb;
          equipoA = element.pequipoa;
          equipoB = element.pequipob;
          this.equipoA = element.pequipoa;
          this.equipoB = element.pequipob;
          this.inpTorneoHora = element.ptime;
          this.inpTorneoFecha = element.pdate;
          this.inpTorneoChancha = element.pcancha;
          break;
        }
      }

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.enombre == equipoA) {
          idA = element._id;
          break;
        }
      }

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.enombre == equipoB) {
          idB = element._id;
          break;
        }
      }

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.jequipo == idA) {
          this.lstJugadoresA.push({
            jnombre: element.jnombre,
            japellido: element.japellido,
            amonestaciones: element.jamonestaciones,
            id: element._id,
          });
        }
      }

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.jequipo == idB) {
          this.lstJugadoresB.push({
            jnombre: element.jnombre,
            japellido: element.japellido,
            amonestaciones: element.jamonestaciones,
            id: element._id,
          });
        }
      }
    },

    fnTorneoGuardarPartidos() {
      this.loader10 = true;
      this.success10 = false;
      const test = this.$refs.fotosPartido.files[0];
      let formData = new FormData();
      this.data = new Data();
      this.data.pfpa = this.fairPlayEquipoA;
      this.data.pfpb = this.fairPlayEquipoB;

      console.log(test);

      if (test != undefined) {
        formData.append("title", this.partidoId);

        for (let i = 0; i < this.$refs.fotosPartido.files.length; i++) {
          const foto = this.$refs.fotosPartido.files[i];
          formData.append("image", foto);
        }
        axios.post(this.apiImg, formData).then((res) => {
          console.log(res);
          formData = new FormData();
        });
      }

      if (this.golesEquipoB != "") {
        this.data.peagoles = this.golesEquipoA;
      }

      if (this.golesEquipoB != "") {
        this.data.pebgoles = this.golesEquipoB;
      }

      axios.put(this.api + "/" + this.partidoId, this.data).then((res) => {
        console.log(res);
        axios.get(this.api).then((res) => {
          this.datos = res.data;
          this.loader10 = false;
          this.success10 = true;
        });
      });
    },
    fnPartidoDetalles() {
      if (this.partidoDetalles) {
        this.partidoDetalles = false;
      } else {
        this.partidoDetalles = true;
      }

      for (let i = 0; i < this.lstJugadoresA.length; i++) {
        const element = this.lstJugadoresA[i];
        if (parseInt(element.amonestaciones) > 0) {
          this.lstAmonestadosA.push({
            id: element.id,
            jnombre: element.jnombre,
            japellido: element.japellido,
            amonestaciones: element.amonestaciones,
          });
        }
      }

      for (let i = 0; i < this.lstJugadoresB.length; i++) {
        const element = this.lstJugadoresB[i];
        if (parseInt(element.amonestaciones) > 0) {
          this.lstAmonestadosB.push({
            id: element.id,
            jnombre: element.jnombre,
            japellido: element.japellido,
            amonestaciones: element.amonestaciones,
          });
        }
      }
    },
    fnPartidoDetallesGuardar() {
      this.loader11 = true;
      let soloA = false;
      let soloB = false;
      let ambos = false;
      let existente = false;
      let existeA = false;
      let existeB = false;
      let partidos = [];
      let playerA = "";
      let playerB = "";
      let amarillasA = 0;
      let rojasA = 0;
      let amarillasB = 0;
      let rojasB = 0;
      let datosJA = [];
      let datosJB = [];
      let datoAmarillaA = 0;
      let datoAmarillaB = 0;

      if (
        this.golesJugadorA != "" ||
        this.chekedA1 ||
        this.chekedA2 ||
        this.chekedA3
      ) {
        soloA = true;
      }

      if (
        this.golesJugadorB != "" ||
        this.chekedB1 ||
        this.chekedB2 ||
        this.chekedB3
      ) {
        soloB = true;
      }

      if (soloA && soloB) {
        ambos = true;
        soloA = false;
        soloB = false;
      }

      if (this.chekedA1) {
        amarillasA = 1;
      }

      if (this.chekedA2) {
        amarillasA = 2;
      }

      if (this.chekedA3) {
        rojasA = 1;
      }

      if (this.chekedB1) {
        amarillasB = 1;
      }

      if (this.chekedB2) {
        amarillasB = 2;
      }

      if (this.chekedB3) {
        rojasB = 1;
      }

      if (soloA) {
        console.log("Solo A");

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element.epartidoid == this.partidoId) {
            partidos.push({
              epartidoid: element.epartidoid,
              eequipo: element.eequipo,
              ejugador: element.ejugador,
              egoles: element.egoles,
              eamarillas: element.eamarillas,
              erojas: element.erojas,
              id: element._id,
            });
          }
        }

        for (let i = 0; i < partidos.length; i++) {
          const element = partidos[i];
          if (element.ejugador == this.jugadorA) {
            existente = true;
            playerA = element.id;
            break;
          }
        }

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element._id == this.jugadorA) {
            datosJA.push({
              id: element._id,
              jamonestaciones: element.jamonestaciones,
              jtarjetasam: element.jtarjetasam,
              jnombre: element.jnombre,
              japellido: element.japellido,
            });
            this.idJugadorA = element._id;
            break;
          }
        }

        if (datosJA[0].jtarjetasam <= 2) {
          datoAmarillaA = parseInt(datosJA[0].jtarjetasam) + amarillasA;
        }

        if (datoAmarillaA >= 3) {
          alert(
            datosJA[0].jnombre +
              " " +
              datosJA[0].japellido +
              " " +
              "a superado el límite de tarjetas acumuladas. Indique partidos de suspención."
          );
          this.amonestacionA = false;
        }

        if (datoAmarillaA < 3) {
          this.data = new Data();
          this.data.jtarjetasam = datoAmarillaA;

          axios.put(this.api + "/" + this.idJugadorA, this.data).then((res) => {
            console.log(res);
          });
        }

        if (rojasA > 0) {
          alert(
            datosJA[0].jnombre +
              " " +
              datosJA[0].japellido +
              " " +
              "a recivido una tarjeta roja. Indique partidos de suspención."
          );
          this.amonestacionA = false;
        }

        if (existente) {
          console.log("Solo A - Existente");

          this.data = new Data();
          this.data.epartidoid = this.partidoId;
          this.data.eequipo = this.equipoA;
          this.data.ejugador = this.jugadorA;
          this.data.egoles = this.golesJugadorA;
          this.data.eamarillas = amarillasA;
          this.data.erojas = rojasA;

          axios.put(this.api + "/" + playerA, this.data).then((res) => {
            console.log(res);
            axios.get(this.api).then((res) => {
              this.datos = res.data;
              this.loader11 = false;
              this.success11 = true;
              this.golesJugadorA = "";
              this.jugadorA = "";
              this.chekedA4 = true;
              this.chekedA3 = false;
              this.chekedA2 = false;
              this.chekedA1 = false;
            });
          });
        }

        if (!existente) {
          console.log("Solo A - No existente");

          this.data = new Data();
          this.data.epartidoid = this.partidoId;
          this.data.eequipo = this.equipoA;
          this.data.ejugador = this.jugadorA;
          this.data.egoles = this.golesJugadorA;
          this.data.eamarillas = amarillasA;
          this.data.erojas = rojasA;

          axios.post(this.api, this.data).then((res) => {
            console.log(res);
            axios.get(this.api).then((res) => {
              this.datos = res.data;
              this.loader11 = false;
              this.success11 = true;
              this.golesJugadorA = "";
              this.jugadorA = "";
              this.chekedA4 = true;
              this.chekedA3 = false;
              this.chekedA2 = false;
              this.chekedA1 = false;
            });
          });
        }
      }

      if (soloB) {
        console.log("Solo B");

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element.epartidoid == this.partidoId) {
            partidos.push({
              epartidoid: element.epartidoid,
              eequipo: element.eequipo,
              ejugador: element.ejugador,
              egoles: element.egoles,
              eamarillas: element.eamarillas,
              erojas: element.erojas,
              id: element._id,
            });
          }
        }

        for (let i = 0; i < partidos.length; i++) {
          const element = partidos[i];
          if (element.ejugador == this.jugadorB) {
            existente = true;
            playerB = element.id;
            break;
          }
        }

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element._id == this.jugadorB) {
            datosJB.push({
              id: element._id,
              jamonestaciones: element.jamonestaciones,
              jtarjetasam: element.jtarjetasam,
              jnombre: element.jnombre,
              japellido: element.japellido,
            });
            this.idJugadorB = element._id;
            break;
          }
        }

        if (datosJB[0].jtarjetasam <= 2) {
          datoAmarillaB = parseInt(datosJB[0].jtarjetasam) + amarillasB;
        }

        if (datoAmarillaB >= 3) {
          alert(
            datosJB[0].jnombre +
              " " +
              datosJB[0].japellido +
              " " +
              "a superado el límite de tarjetas acumuladas."
          );
          this.amonestacionB = false;
        }

        if (datoAmarillaB < 3) {
          this.data = new Data();
          this.data.jtarjetasam = datoAmarillaB;

          axios.put(this.api + "/" + this.idJugadorB, this.data).then((res) => {
            console.log(res);
          });
        }

        if (rojasB > 0) {
          alert(
            datosJB[0].jnombre +
              " " +
              datosJB[0].japellido +
              " " +
              "a recivido una tarjeta roja. Indique partidos de suspención."
          );
          this.amonestacionB = false;
        }

        if (existente) {
          console.log("Solo B - Existente");

          this.data = new Data();
          this.data.epartidoid = this.partidoId;
          this.data.eequipo = this.equipoB;
          this.data.ejugador = this.jugadorB;
          this.data.egoles = this.golesJugadorB;
          this.data.eamarillas = amarillasB;
          this.data.erojas = rojasB;

          axios.put(this.api + "/" + playerB, this.data).then((res) => {
            console.log(res);
            axios.get(this.api).then((res) => {
              this.datos = res.data;
              this.loader11 = false;
              this.success11 = true;
              this.golesJugadorB = "";
              this.jugadorB = "";
              this.chekedB4 = true;
              this.chekedB3 = false;
              this.chekedB2 = false;
              this.chekedB1 = false;
            });
          });
        }

        if (!existente) {
          console.log("Solo B - No existente");

          this.data = new Data();
          this.data.epartidoid = this.partidoId;
          this.data.eequipo = this.equipoB;
          this.data.ejugador = this.jugadorB;
          this.data.egoles = this.golesJugadorB;
          this.data.eamarillas = amarillasB;
          this.data.erojas = rojasB;

          axios.post(this.api, this.data).then((res) => {
            console.log(res);
            axios.get(this.api).then((res) => {
              this.datos = res.data;
              this.loader11 = false;
              this.success11 = true;
              this.golesJugadorB = "";
              this.jugadorB = "";
              this.chekedB4 = true;
              this.chekedB3 = false;
              this.chekedB2 = false;
              this.chekedB1 = false;
            });
          });
        }
      }

      if (ambos) {
        console.log("Ambos");

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element.epartidoid == this.partidoId) {
            partidos.push({
              epartidoid: element.epartidoid,
              eequipo: element.eequipo,
              ejugador: element.ejugador,
              egoles: element.egoles,
              eamarillas: element.eamarillas,
              erojas: element.erojas,
              id: element._id,
            });
          }
        }

        for (let i = 0; i < partidos.length; i++) {
          const element = partidos[i];
          if (element.ejugador == this.jugadorA) {
            existeA = true;
            playerA = element.id;
          } else if (element.ejugador == this.jugadorB) {
            existeB = true;
            playerB = element.id;
          }
        }

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element._id == this.jugadorB) {
            datosJB.push({
              id: element._id,
              jamonestaciones: element.jamonestaciones,
              jtarjetasam: element.jtarjetasam,
              jnombre: element.jnombre,
              japellido: element.japellido,
            });
            this.idJugadorB = element._id;
            break;
          }
        }

        if (datosJB[0].jtarjetasam <= 2) {
          datoAmarillaB = parseInt(datosJB[0].jtarjetasam) + amarillasB;
        }

        if (datoAmarillaB >= 3) {
          alert(
            datosJB[0].jnombre +
              " " +
              datosJB[0].japellido +
              " " +
              "a superado el límite de tarjetas acumuladas."
          );
          this.amonestacionB = false;
        }

        if (datoAmarillaB < 3) {
          this.data = new Data();
          this.data.jtarjetasam = datoAmarillaB;

          axios.put(this.api + "/" + this.idJugadorA, this.data).then((res) => {
            console.log(res);
          });
        }

        if (rojasB > 0) {
          alert(
            datosJB[0].jnombre +
              " " +
              datosJB[0].japellido +
              " " +
              "a recivido una tarjeta roja. Indique partidos de suspención."
          );
          this.amonestacionB = false;
        }

        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element._id == this.jugadorA) {
            datosJA.push({
              id: element._id,
              jamonestaciones: element.jamonestaciones,
              jtarjetasam: element.jtarjetasam,
              jnombre: element.jnombre,
              japellido: element.japellido,
            });
            this.idJugadorA = element._id;
            break;
          }
        }

        if (datosJA[0].jtarjetasam <= 2) {
          datoAmarillaA = parseInt(datosJA[0].jtarjetasam) + amarillasA;
        }

        if (datoAmarillaA >= 3) {
          alert(
            datosJA[0].jnombre +
              " " +
              datosJA[0].japellido +
              " " +
              "a superado el límite de tarjetas acumuladas. Indique partidos de suspención."
          );
          this.amonestacionA = false;
        }

        if (datoAmarillaA < 3) {
          this.data = new Data();
          this.data.jtarjetasam = datoAmarillaA;

          axios.put(this.api + "/" + this.idJugadorA, this.data).then((res) => {
            console.log(res);
          });
        }

        if (rojasA > 0) {
          alert(
            datosJA[0].jnombre +
              " " +
              datosJA[0].japellido +
              " " +
              "a recivido una tarjeta roja. Indique partidos de suspención."
          );
          this.amonestacionA = false;
        }

        console.log(playerB);
        console.log(playerA);

        if (existeA && !existeB) {
          console.log("Ambos - existe/!existe");

          this.data = new Data();
          this.data.epartidoid = this.partidoId;
          this.data.eequipo = this.equipoA;
          this.data.ejugador = this.jugadorA;
          this.data.egoles = this.golesJugadorA;
          this.data.eamarillas = amarillasA;
          this.data.erojas = rojasA;

          axios.put(this.api + "/" + playerA, this.data).then((res) => {
            console.log(res);

            this.data = new Data();
            this.data.epartidoid = this.partidoId;
            this.data.eequipo = this.equipoB;
            this.data.ejugador = this.jugadorB;
            this.data.egoles = this.golesJugadorB;
            this.data.eamarillas = amarillasB;
            this.data.erojas = rojasB;

            axios.post(this.api, this.data).then((res) => {
              console.log(res);
              axios.get(this.api).then((res) => {
                this.datos = res.data;
                this.loader11 = false;
                this.success11 = true;
                this.golesJugadorB = "";
                this.chekedB4 = true;
                this.chekedB3 = false;
                this.chekedB2 = false;
                this.chekedB1 = false;
                this.golesJugadorA = "";
                this.chekedA4 = true;
                this.chekedA3 = false;
                this.chekedA2 = false;
                this.chekedA1 = false;
              });
            });
          });
        }

        if (!existeA && existeB) {
          console.log("Ambos - !existe/existe");

          this.data = new Data();
          this.data.epartidoid = this.partidoId;
          this.data.eequipo = this.equipoB;
          this.data.ejugador = this.jugadorB;
          this.data.egoles = this.golesJugadorB;
          this.data.eamarillas = amarillasB;
          this.data.erojas = rojasB;

          axios.put(this.api + "/" + playerB, this.data).then((res) => {
            console.log(res);

            this.data = new Data();
            this.data.epartidoid = this.partidoId;
            this.data.eequipo = this.equipoA;
            this.data.ejugador = this.jugadorA;
            this.data.egoles = this.golesJugadorA;
            this.data.eamarillas = amarillasA;
            this.data.erojas = rojasA;

            axios.post(this.api, this.data).then((res) => {
              console.log(res);
              axios.get(this.api).then((res) => {
                this.datos = res.data;
                this.loader11 = false;
                this.success11 = true;
                this.golesJugadorB = "";
                this.chekedB4 = true;
                this.chekedB3 = false;
                this.chekedB2 = false;
                this.chekedB1 = false;
                this.golesJugadorA = "";
                this.chekedA4 = true;
                this.chekedA3 = false;
                this.chekedA2 = false;
                this.chekedA1 = false;
              });
            });
          });
        }

        if (!existeA && !existeB) {
          console.log("Ambos - !existe/!existe");

          this.data = new Data();
          this.data.epartidoid = this.partidoId;
          this.data.eequipo = this.equipoA;
          this.data.ejugador = this.jugadorA;
          this.data.egoles = this.golesJugadorA;
          this.data.eamarillas = amarillasA;
          this.data.erojas = rojasA;

          axios.post(this.api, this.data).then((res) => {
            console.log(res);

            this.data = new Data();
            this.data.epartidoid = this.partidoId;
            this.data.eequipo = this.equipoB;
            this.data.ejugador = this.jugadorB;
            this.data.egoles = this.golesJugadorB;
            this.data.eamarillas = amarillasB;
            this.data.erojas = rojasB;

            axios.post(this.api, this.data).then((res) => {
              console.log(res);
              axios.get(this.api).then((res) => {
                this.datos = res.data;
                this.loader11 = false;
                this.success11 = true;
                this.golesJugadorB = "";
                this.chekedB4 = true;
                this.chekedB3 = false;
                this.chekedB2 = false;
                this.chekedB1 = false;
                this.golesJugadorA = "";
                this.chekedA4 = true;
                this.chekedA3 = false;
                this.chekedA2 = false;
                this.chekedA1 = false;
              });
            });
          });
        }

        if (existeA && existeB) {
          console.log("Ambos - existe/existe");

          this.data = new Data();
          this.data.epartidoid = this.partidoId;
          this.data.eequipo = this.equipoA;
          this.data.ejugador = this.jugadorA;
          this.data.egoles = this.golesJugadorA;
          this.data.eamarillas = amarillasA;
          this.data.erojas = rojasA;

          axios.put(this.api + "/" + playerA, this.data).then((res) => {
            console.log(res);

            this.data = new Data();
            this.data.epartidoid = this.partidoId;
            this.data.eequipo = this.equipoB;
            this.data.ejugador = this.jugadorB;
            this.data.egoles = this.golesJugadorB;
            this.data.eamarillas = amarillasB;
            this.data.erojas = rojasB;

            axios.put(this.api + "/" + playerB, this.data).then((res) => {
              console.log(res);
              axios.get(this.api).then((res) => {
                this.datos = res.data;
                this.loader11 = false;
                this.success11 = true;
                this.golesJugadorB = "";
                this.chekedB4 = true;
                this.chekedB3 = false;
                this.chekedB2 = false;
                this.chekedB1 = false;
                this.golesJugadorA = "";
                this.chekedA4 = true;
                this.chekedA3 = false;
                this.chekedA2 = false;
                this.chekedA1 = false;
              });
            });
          });
        }
      }
      this.fnTorneoSelPartidoData(this.partidoId);
    },

    fnAmonestacionesA() {
      this.data = new Data();
      this.data.jamonestaciones = this.sancionesA;

      axios.put(this.api + "/" + this.idJugadorA, this.data).then((res) => {
        console.log(res);
      });
    },

    fnAmonestacionesB() {
      this.data = new Data();
      this.data.jamonestaciones = this.sancionesB;

      axios.put(this.api + "/" + this.idJugadorB, this.data).then((res) => {
        console.log(res);
      });
    },

    eliminar(id) {
      let pregunta = false;

      pregunta = confirm("Seguro que desea eliminar este elemento?");

      if (pregunta) {
        axios.delete(this.api + "/" + id).then((res) => {
          console.log(res);
          alert("Elemento borrado");
        });
      }
    },

    fnAplicarSanciones() {
      this.btnAplicarSanciones = true;
      this.descontados = true;

      if (this.lstAmonestadosA[0].amonestaciones != undefined) {
        for (let i = 0; i < this.lstAmonestadosA.length; i++) {
          const element = this.lstAmonestadosA[i];
          this.data = new Data();
          this.data.jamonestaciones = parseInt(element.amonestaciones) - 1;

          axios.put(this.api + "/" + element.id, this.data).then((res) => {
            console.log(res);
          });
        }
      }

      if (this.lstAmonestadosB[0].amonestaciones != undefined) {
        for (let i = 0; i < this.lstAmonestadosB.length; i++) {
          const element = this.lstAmonestadosB[i];
          this.data = new Data();
          this.data.jamonestaciones = parseInt(element.amonestaciones) - 1;

          axios.put(this.api + "/" + element.id, this.data).then((res) => {
            console.log(res);
          });
        }
      }
    },

    fnImportarJugador(id, nombre, apellido) {
      let contador = 0;

      this.lstImpJugadores.push({
        id: id,
        nombre: nombre,
        apellido: apellido,
      });

      for (let i = 0; i < this.lstImpJugadores.length; i++) {
        const element = this.lstImpJugadores[i];
        if (element.id == id) {
          contador++;
        }
      }

      if (contador > 1) {
        for (let i = 0; i < this.lstImpJugadores.length; i++) {
          const element = this.lstImpJugadores[i];
          if (element.id == id) {
            this.lstImpJugadores.splice(i, 1);
            break;
          }
        }
      }
    },

    fnGuardarImportados() {
      this.loader12 = true;

      for (let i = 0; i < this.lstImpJugadores.length; i++) {
        const element = this.lstImpJugadores[i];
        this.data = new Data();
        this.data.jequipo = this.selecid;
        axios.put(this.api + "/" + element.id, this.data).then((res) => {
          console.log(res);
          console.log(this.lstImpJugadores.length);
          console.log(i);
        });
        if (this.lstImpJugadores.length == i + 1) {
          axios.get(this.api).then((res) => {
            this.datos = [];
            this.datos = res.data;
            this.loader12 = false;
            this.lstImpJugadores = [];
          });
        }
      }
    },

    fnEliminarImportado(id) {
      for (let i = 0; i < this.lstImpJugadores.length; i++) {
        const element = this.lstImpJugadores[i];
        if (element.id == id) {
          this.lstImpJugadores.splice(i, 1);
          break;
        }
      }
    },

    fnEliminar(id) {
      let eliminar = false;
      eliminar = confirm("Esta seguro de eliminar este registro?");

      if (eliminar) {
        alert(
          "Procediendo a eliminar, por favor aguarde el mensaje de confirmacion para continuar..."
        );
        axios.delete(this.api + "/" + id).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = [];
            this.datos = res.data;
            this.fnTorneoSelPartidoData(this.partidoId);
            alert("Elemento eliminado correctamente...");
          });
        });
      }
    },

    fnEliminarTodasFotos() {
      let eliminar = false;
      eliminar = confirm("Esta seguro de eliminar todas las fotos?");

      if (eliminar) {
        alert(
          "Eliminando... Aguarde mensaje de confirmacion para continuar..."
        );
        for (let i = 0; i < this.lstFotosDetalles.length; i++) {
          const element = this.lstFotosDetalles[i];
          axios.delete(this.api + "/" + element.id).then((res) => {
            console.log(res);
          });
        }
        axios.get(this.api).then((res) => {
          this.datos = [];
          this.datos = res.data;
          this.fnTorneoSelPartidoData(this.partidoId);
          alert("Fotos eliminadas correctamente...");
        });
      }
    },

    fnEditarPartido() {
      this.editarPartido = true;
      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.edivision == this.select3) {
          this.lstEquipos.push({
            id: element._id,
            enombre: element.enombre,
          });
        }
      }
    },

    fnGuardarCambiosPartido() {
      let confirmar = false;
      confirmar = confirm("Desea guardar los cambios?");

      if (confirmar) {
        alert(
          "Guardando datos, por favor espere el mensaje de confirmacion para continuar..."
        );
        this.data = new Data();
        this.data.pequipoa = this.equipoA;
        this.data.pequipob = this.equipoB;
        this.data.pcancha = this.inpTorneoChancha;
        this.data.pdate = this.inpTorneoFecha;
        this.data.ptime = this.inpTorneoHora;

        axios.put(this.api + "/" + this.partidoId, this.data).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = [];
            this.datos = res.api;
            alert(
              "Partido guardado, por favor re-seleccione la fecha para actualizar los partidos..."
            );
          });
        });
      }
    },

    fnEliminarPartido() {
      let confirmar = false;
      confirmar = confirm("Desea eliminar el partido?");

      if (confirmar) {
        alert(
          "Eliminando partido... por favor aguarde mensaje de confirmacion para continuar..."
        );
        axios.delete(this.api + "/" + this.partidoId).then((res) => {
          console.log(res);
          axios.get(this.api).then((res) => {
            this.datos = [];
            this.datos = res.data;
            alert(
              "Partido eliminado por favor re-seleccione la fecha para actualizar la lista..."
            );
          });
        });
      }
    },
  },

  computed: {
    cplstDivisionales: function () {
      return _.sortBy(this.lstDivisionales, ["divisional"]);
    },
    cplstEquipos: function () {
      return _.sortBy(this.lstEquipos, ["enombre"]);
    },
    cplstJugadores: function () {
      return _.sortBy(this.lstJugadores, ["jnombre"]);
    },
    cplstDivisionalesImportar: function () {
      return _.sortBy(this.lstDivisionalesImportar, ["divisional"]);
    },
    cplstEquiposImportar: function () {
      return _.sortBy(this.lstEquiposImportar, ["enombre"]);
    },
    cplstJugadoresImportar: function () {
      return _.sortBy(this.lstJugadoresImportar, ["jnombre"]);
    },
    cplstTorneos: function () {
      return _.sortBy(this.lstTorneos, ["tnombre"]);
    },
    cplstFechas: function () {
      return _.sortBy(this.lstFechas, ["fnombre"]);
    },
    cplstJugadoresA: function () {
      return _.sortBy(this.lstJugadoresA, ["jnombre", "japellido"]);
    },
    cplstJugadoresB: function () {
      return _.sortBy(this.lstJugadoresB, ["jnombre", "japellido"]);
    },
  },
};
</script>