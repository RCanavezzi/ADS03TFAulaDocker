use MyMongoDB
switched to db MyMongoDB

/////Exercício 1: Inserindo Dados
db.client.insertMany{[{
  "full_name": "Maria Silva",
  "cpf": "12345678901",
  "email": "maria.silva@email.com",
  "phone": "11987654321",
  "address": "Rua das Flores, 123",
  "city": "São Paulo",
  "state": "SP",
  "zip_code": "01001000",
  "created_by": "user_id_do_admin_1",
  "enterprise": null,
  "cnpj_enterprise": null,
  "description": "Cliente individual"
},
{
  "full_name": "Empresa Soluções Ltda",
  "cpf": null,
  "email": "contato@solucoes.com.br",
  "phone": "21998765432",
  "address": "Avenida Principal, 456",
  "city": "Rio de Janeiro",
  "state": "RJ",
  "zip_code": "20010020",
  "created_by": "user_id_do_manager_2",
  "enterprise": "Soluções Ltda",
  "cnpj_enterprise": "12345678000190",
  "description": "Cliente corporativo"
}]}

db.client.insertOne({
  "full_name": "Maria Silva",
  "cpf": "12345678901",
  "email": "maria.silva@email.com",
  "phone": "11987654321",
  "address": "Rua das Flores, 123",
  "city": "São Paulo",
  "state": "SP",
  "zip_code": "01001000",
  "created_by": "user_id_do_admin_1",
  "enterprise": null,
  "cnpj_enterprise": null,
  "description": "Cliente individual"
})
{
  acknowledged: true,
  insertedId: ObjectId('68098327c49e8ce7c0eba98d')
}
db.client.insertOne({
  "full_name": "Empresa Soluções Ltda",
  "cpf": null,
  "email": "contato@solucoes.com.br",
  "phone": "21998765432",
  "address": "Avenida Principal, 456",
  "city": "Rio de Janeiro",
  "state": "RJ",
  "zip_code": "20010020",
  "created_by": "user_id_do_manager_2",
  "enterprise": "Soluções Ltda",
  "cnpj_enterprise": "12345678000190",
  "description": "Cliente corporativo"
})
{
  acknowledged: true,
  insertedId: ObjectId('6809834cc49e8ce7c0eba98e')
}
db.client_processes.insertOne{ "client_id": "id_do_cliente_maria_silva",
  "number": "PROC-2023-001",
  "value": 1500.00,
  "status": "ativo",
  "class": "Cobrança",
  "description": "Processo de cobrança referente a fatura em aberto.",
  "created_at": ISODate("2023-10-26T10:00:00Z")}

db.client_processes.insertOne({ "client_id": "id_do_cliente_maria_silva",
  "number": "PROC-2023-001",
  "value": 1500.00,
  "status": "ativo",
  "class": "Cobrança",
  "description": "Processo de cobrança referente a fatura em aberto.",
  "created_at": ISODate("2023-10-26T10:00:00Z")})
{
  acknowledged: true,
  insertedId: ObjectId('680983dfc49e8ce7c0eba98f')
}
db.client_processes.insertOne({
  "client_id": "id_do_cliente_empresa_solucoes",
  "number": "PROC-2023-002",
  "value": 5500.50,
  "status": "em análise",
  "class": "Contratual",
  "description": "Análise de contrato de prestação de serviços.",
  "created_at": ISODate("2023-11-15T14:30:00Z")
})
{
  acknowledged: true,
  insertedId: ObjectId('680983f5c49e8ce7c0eba990')
}
db.events.insertMany([{
  "client_id": "id_do_cliente_maria_silva",
  "enterprise": null,
  "cnpj_enterprise": null,
  "freight": 50.00,
  "amount_of_cleaning": 2,
  "cleaning_date": "2023-12-10",
  "cost_of_each_cleanin": 200.00,
  "proposal_doc": "PROP-MS-001.pdf",
  "number_proposal": "PROP-2023-001-MS",
  "proposal_expiration_date": ISODate("2023-11-30T23:59:59Z"),
  "created_proposal_by": "user_id_do_sales_3",
  "address": "Rua das Camélias, 789",
  "city": "São Paulo",
  "state": "SP",
  "zip_code": "02002000",
  "proposal_status": "accepted"
}, {
  "client_id": "id_do_cliente_empresa_solucoes",
  "enterprise": "Soluções Ltda",
  "cnpj_enterprise": "12345678000190",
  "freight": 120.00,
  "amount_of_cleaning": 5,
  "cleaning_date": "2024-01-15",
  "cost_of_each_cleanin": 150.00,
  "proposal_doc": "PROP-ESL-002.pdf",
  "number_proposal": "PROP-2023-002-ESL",
  "proposal_expiration_date": ISODate("2023-12-20T23:59:59Z"),
  "created_proposal_by": "user_id_do_sales_3",
  "address": "Avenida das Palmeiras, 1011",
  "city": "Rio de Janeiro",
  "state": "RJ",
  "zip_code": "22020030",
  "proposal_status": "pending accepted"
}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6809859dc49e8ce7c0eba991'),
    '1': ObjectId('6809859dc49e8ce7c0eba992')
  }
}

////Exercício 2: Consultando Dados

//////////Clientes em São Paulo: 
db.client.find({city:"São Paulo"});
{
  _id: ObjectId('68098327c49e8ce7c0eba98d'),
  full_name: 'Maria Silva',
  cpf: '12345678901',
  email: 'maria.silva@email.com',
  phone: '11987654321',
  address: 'Rua das Flores, 123',
  city: 'São Paulo',
  state: 'SP',
  zip_code: '01001000',
  created_by: 'user_id_do_admin_1',
  enterprise: null,
  cnpj_enterprise: null,
  description: 'Cliente individual'
}
//////////Processos com Valor Superior a:
db.client_processes.find({value:{$gt:2000}})
{
  _id: ObjectId('680983f5c49e8ce7c0eba990'),
  client_id: 'id_do_cliente_empresa_solucoes',
  number: 'PROC-2023-002',
  value: 5500.5,
  status: 'em análise',
  class: 'Contratual',
  description: 'Análise de contrato de prestação de serviços.',
  created_at: 2023-11-15T14:30:00.000Z
}
///////////Eventos com Proposta Pendente ou Aceita:

db.events.find(
  {
    "$or": [
      { "proposal_status":  "pending accepted"  }, { "proposal_status": "accepted"}
    ]
  });
 
{
  _id: ObjectId('6809859dc49e8ce7c0eba991'),
  client_id: 'id_do_cliente_maria_silva',
  enterprise: null,
  cnpj_enterprise: null,
  freight: 50,
  amount_of_cleaning: 2,
  cleaning_date: '2023-12-10',
  cost_of_each_cleanin: 200,
  proposal_doc: 'PROP-MS-001.pdf',
  number_proposal: 'PROP-2023-001-MS',
  proposal_expiration_date: 2023-11-30T23:59:59.000Z,
  created_proposal_by: 'user_id_do_sales_3',
  address: 'Rua das Camélias, 789',
  city: 'São Paulo',
  state: 'SP',
  zip_code: '02002000',
  proposal_status: 'accepted'
}
{
  _id: ObjectId('6809859dc49e8ce7c0eba992'),
  client_id: 'id_do_cliente_empresa_solucoes',
  enterprise: 'Soluções Ltda',
  cnpj_enterprise: '12345678000190',
  freight: 120,
  amount_of_cleaning: 5,
  cleaning_date: '2024-01-15',
  cost_of_each_cleanin: 150,
  proposal_doc: 'PROP-ESL-002.pdf',
  number_proposal: 'PROP-2023-002-ESL',
  proposal_expiration_date: 2023-12-20T23:59:59.000Z,
  created_proposal_by: 'user_id_do_sales_3',
  address: 'Avenida das Palmeiras, 1011',
  city: 'Rio de Janeiro',
  state: 'RJ',
  zip_code: '22020030',
  proposal_status: 'pending accepted'
}
////////////Clientes Corporativos:

db.client.find({enterprise:{$ne:null}},{ "full_name": 1, "cnpj_enterprise": 1, "_id": 0 })
{
  full_name: 'Empresa Soluções Ltda',
  cnpj_enterprise: '12345678000190'
}

//////Exercício 3: Atualizando Dados

////////Atualizar Status do Processo: 
db.client_processes.updateOne(
  { "number": "PROC-2023-001" },
  { "$set": { "number": "concluído" } }
);
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
db.client_processes.find({ "number": "concluído" });
{
  _id: ObjectId('680983dfc49e8ce7c0eba98f'),
  client_id: 'id_do_cliente_maria_silva',
  number: 'concluído',
  value: 1500,
  status: 'ativo',
  class: 'Cobrança',
  description: 'Processo de cobrança referente a fatura em aberto.',
  created_at: 2023-10-26T10:00:00.000Z
}

/////////Adicionar Observação ao Evento: 
db.events.updateOne({client_id:"id_do_cliente_maria_silva"},{$set:{"note_doc": "OBS-MS-001.txt"}})
